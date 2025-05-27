<script>
  import { onMount } from 'svelte';
  import { sankey, sankeyLinkHorizontal } from 'd3-sankey';
  import { select } from 'd3-selection';
  import { scaleOrdinal } from 'd3-scale';

  /** @type {{[k:string]: Array<Record<string,any>>}} */
  export let datasets;

  // You can tweak these defaults from the parent via bind:this if needed
  export let width = 960;
  export let height = 520;
  export let onLinkClick = null; // Add this at the top with your other exports

  let svg;

  // simple colour palette matching the mock‑up screenshot
  const colour = scaleOrdinal()
    .domain(['Lawsuit', 'Licensing', 'Other Deal'])
    .range(['#d6613b', '#9aa27d', '#b7d3f3']);

  // -----------------------------------------------------------
  // Build / rebuild the diagram whenever `datasets` changes
  // -----------------------------------------------------------
  function build() {
    if (!datasets) return;

    /* ---------------------------------
       1. Flatten → aggregate → graph
    ---------------------------------*/
    const nodes = [];
    const nodeIdx = new Map();
    const links = [];
    const sourceOrder = ['Lawsuit', 'Licensing', 'Other Deal'];


    // helper to get (or lazily create) a node id
    const id = (name) => {
      if (!nodeIdx.has(name)) {
        nodeIdx.set(name, nodes.length);
        nodes.push({ name });
      }
      return nodeIdx.get(name);
    };

    for (const group of Object.keys(datasets)) {
      const records = datasets[group] || [];
      const sourceName = group.replace(/s$/, ''); // "Lawsuits" → "Lawsuit"
      const s = id(sourceName);

      records.forEach((r) => {
        const platforms = Array.isArray(r.Platform)
        ? r.Platform.map(p => p.trim())
        : [r.Platform.trim()];

      for (const platform of platforms) {
        const t = id(platform);
        const existing = links.find((l) => l.source === s && l.target === t);
        if (existing) existing.value += 1;
        else links.push({ source: s, target: t, value: 1, cat: sourceName });
      }

      });
    }

    /* ----------------------------
       2. Run D3‑Sankey layout
    ----------------------------*/
    const margin = { left: 80, right: 150, top: 30, bottom: 30 }; // adjust left as needed

    const sankeyGen = sankey()
      .nodeWidth(5)
      // .nodePadding(28)
      .extent([
        [margin.left, margin.top],
        [width - margin.right, height - margin.bottom]
      ]);

    const graph = sankeyGen({
      nodes: nodes.map((d) => ({ ...d })),
      links: links.map((d) => ({ ...d }))
    });

    // Reorder source (depth 0) nodes vertically
    const sourceNodes = graph.nodes.filter(n => n.depth === 0);

    // Sort based on sourceOrder
    sourceNodes.sort((a, b) => sourceOrder.indexOf(a.name) - sourceOrder.indexOf(b.name));

    // Set new Y positions manually
    let yCursor = margin.top;
    const nodePadding = 20; // or 30 if spacing is still tight

    for (const node of sourceNodes) {
      const height = node.y1 - node.y0;
      node.y0 = yCursor;
      node.y1 = yCursor + height;
      yCursor = node.y1 + nodePadding;
    }


    // Update layout with new node positions
    sankeyGen.update(graph);

    /* ----------------------------
       3. Render SVG elements
    ----------------------------*/
    const root = select(svg);
    root.selectAll('*').remove();
    root.attr('viewBox', `0 0 ${width} ${height}`);

    // links (back‑to‑front so wider links don’t overlap narrow ones)
    // Tooltip selection
    const tooltip = select('#sankey-tooltip');

    // --- LINKS ---
    // When rendering links, give each a class for easy selection:
    const linkSelection = root
      .append('g')
      .attr('fill', 'none')
      .selectAll('path')
      .data(graph.links)
      .join('path')
      .attr('class', 'sankey-link')
      .attr('d', sankeyLinkHorizontal())
      .attr('stroke', d => colour(d.cat))
      .attr('stroke-opacity', 0.75)
      .attr('stroke-width', d => Math.max(1, d.width))
      
      .on('mouseover', function (event, d) {
        // Highlight only the hovered link
        root.selectAll('.sankey-link')
          .attr('stroke-opacity', l => (l === d ? 1 : 0.15))
          .attr('stroke-width', l => (l === d ? Math.max(3, d.width + 2) : Math.max(1, l.width)));

        let label = '';
        if (d.cat === 'Lawsuit') {
          label = `Number of <span style="font-weight:600; color:#d6613b;">lawsuits</span> against <span style="font-weight:600;">${d.target.name}</span>:`;
        } else if (d.cat === 'Licensing') {
          label = `Number of <span style="font-weight:600; color:#9aa27d;">licensing deals</span> between publishers and <span style="font-weight:600;">${d.target.name}</span>:`;
        } else {
          label = `Number of <span style="font-weight:600; color:#b7d3f3;">non-licensing deals</span> involving <span style="font-weight:600;">${d.target.name}</span>:`;
        }

        tooltip
          .style('display', 'block')
          .html(
            `${label}<br><span style="font-weight:600;">${d.value}</span>`
          );
      })
      .on('mousemove', function (event) {
        tooltip
          .style('left', (event.pageX + 16) + 'px')
          .style('top', (event.pageY - 24) + 'px');
      })
      .on('mouseleave', function (event, d) {
        // Reset all links
        root.selectAll('.sankey-link')
          .attr('stroke-opacity', 0.75)
          .attr('stroke-width', l => Math.max(1, l.width));
        tooltip.style('display', 'none');
      })
      .on('click', function(event, d) {
        if (onLinkClick) onLinkClick(d); // Call the callback with the link data
      });

    // --- NODES ---
    // When rendering nodes:
    root
      .append('g')
      .selectAll('rect')
      .data(graph.nodes)
      .join('rect')
      .attr('x', d => d.x0)
      .attr('y', d => d.y0)
      .attr('width', d => d.x1 - d.x0)
      .attr('height', d => d.y1 - d.y0)
      .attr('fill', d => (d.depth === 0 ? colour(d.name) : '#fff'))
      .attr('stroke', '#b5b5b5')
      .on('mouseover', function (event, d) {
        // Highlight all links connected to this node
        root.selectAll('.sankey-link')
          .attr('stroke-opacity', l =>
            l.source === d || l.target === d ? 1 : 0.15
          )
          .attr('stroke-width', l =>
            l.source === d || l.target === d ? Math.max(3, l.width + 2) : Math.max(1, l.width)
          );
        // Optionally, highlight the node itself
        d3.select(this).attr('stroke', '#222').attr('stroke-width', 2);
      })
      .on('mouseleave', function (event, d) {
        // Reset all links
        root.selectAll('.sankey-link')
          .attr('stroke-opacity', 0.75)
          .attr('stroke-width', l => Math.max(1, l.width));
        d3.select(this).attr('stroke', '#b5b5b5').attr('stroke-width', 1);
      });

    // labels
    root
      .append('g')
      .selectAll('text')
      .data(graph.nodes)
      .join('text')
      .attr('x', (d) => (d.depth === 0 ? d.x0 - 8 : d.x1 + 8))
      .attr('y', (d) => (d.y0 + d.y1) / 2)
      .attr('dy', '0.35em')
      .attr('text-anchor', (d) => (d.depth === 0 ? 'end' : 'start'))
      .attr('class', 'sankey-label')
      .text((d) => d.name);

  }

  // initial draw
  onMount(build);
  // redraw whenever `datasets` prop updates
  $: datasets && build();
</script>

<svg class="sankey-diagram" bind:this={svg}></svg>
<div id="sankey-tooltip"></div>

<style>

  :global(.sankey-label) {
    font-family: "Helvetica Neue", Arial, sans-serif;
    font-size: 12px;
  }

  .sankey-diagram {
    width: 100%;
    height: auto;
  }

  #sankey-tooltip {
    position: absolute;
    pointer-events: none;
    background: #fff;
    color: #374151;
    border: 1px solid #43485A;
    padding: 0.75rem 1rem;
    font-size: 0.95em;
    font-family: 'Helvetica Neue', sans-serif;
    display: none;
    z-index: 100;
    opacity: 0.97;
    letter-spacing: 0.01em;
    line-height: 1.5;
    transition: opacity 0.2s;
    max-width: 320px;
    width: max-content;
  }

  .sankey-label {
    font-family: "Helvetica Neue", Arial, sans-serif;
    font-size: 20px;
  }
  
</style>
