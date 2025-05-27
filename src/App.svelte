<script>

  import { fade } from 'svelte/transition';
  import SankeyDiagram from './components/SankeyChart.svelte';


  /** @typedef {Object} Deal */

  const datasets = {
    Lawsuits: [
  {
    "Date": "5/1/2020",
    "Platform": "Ross Intelligence",
    "Partner": "Thomson Reuters",
    "Deal type": "copyright infringement",
    "Reported Details": "Thomson Reuters wins the first major AI copyright case in the U.S. against legal AI startup Ross Intelligence. The judge ruled that Thomson Reuters' copyright was infringed when Ross Intelligence reproduced materials from its legal research firm Westlaw",
    "Press Release(s)": "['https://www.wired.com/story/thomson-reuters-ai-copyright-lawsuit/']"
  },
  {
    "Date": "12/1/2023",
    "Platform": ["OpenAI", "Microsoft"],
    "Partner": "New York Times",
    "Deal type": "copyright infringement",
    "Reported Details": "New York Times files a lawsuit against OpenAI and Microsoft for copyright infringement in a legal battle that could define the value of news content in AI training models",
    "Press Release(s)": "['https://www.axios.com/2023/12/27/nyt-microsoft-openai-lawsuit-copyright-infringement']"
  },
 
  {
    "Date": "2/1/2024",
    "Platform": "OpenAI",
    "Partner": "Raw Story, AlterNet",
    "Deal type": "copyright infringement",
    "Reported Details": "Raw Story and AlterNet sue OpenAI for copyright infringemen saying the company trained its chatbots using copyrighted works without properly citing them. The companies are seeking damages in the amount of at least $2,500 per violation, as well as asking OpenAI to remove all copyrighted articles from data training sets",
    "Press Release(s)": "['https://www.nytimes.com/2024/02/28/technology/openai-copyright-suit-media.html']"
  },
  {
    "Date": "2/1/2024",
    "Platform": ["OpenAI", "Microsoft"],
    "Partner": "The Intercept",
    "Deal type": "copyright infringement",
    "Reported Details": "The Intercept sues OpenAI and Microsoft for developing their chatbots using its copyrighted information",
    "Press Release(s)": "['https://www.nytimes.com/2024/02/28/technology/openai-copyright-suit-media.html']"
  },
 
  {
    "Date": "4/1/2024",
    "Platform": ["OpenAI", "Microsoft"],
    "Partner": "Alden Global Capital",
    "Deal type": "copyright infringement",
    "Reported Details": "Eight prominent U.S. newspapers owned by investment giant Alden Global Capital - the New York Daily News, Chicago Tribune, Orlando Sentinel, South Florida Sun Sentinel, San Jose Mercury News, Denver Post, Orange County Register and St. Paul Pioneer Press - sue OpenAI and Microsoft for copyright infringement, in a complaint filed in the Southern District of New York",
    "Press Release(s)": "['https://apnews.com/article/chatgpt-newspaper-copyright-lawsuit-openai-microsoft-2d5f52d1a720e0a8fa6910dfd59584a9']"
  },
  {
    "Date": "6/1/2024",
    "Platform": ["OpenAI", "Microsoft"],
    "Partner": "Center for Investigative Reporting",
    "Deal type": "copyright infringement",
    "Reported Details": "The Center for Investigative Reporting, which produces Mother Jones and Reveal, sues OpenAI and its largest shareholder, Microsoft, in federal court for using the nonprofit news organizations' content without permission or offering compensation",
    "Press Release(s)": "['https://apnews.com/article/ai-media-lawsuits-center-for-investigative-reporting-chatgpt-mother-jones-c48452889750479410b65a119537746c?recip_id=2167509&lyt_id=2167509']"
  },
  
  {
    "Date": "7/1/2024",
    "Platform": "OpenAI",
    "Partner": "Mumsnet",
    "Deal type": "copyright infringement",
    "Reported Details": "UK parenting website Mumsnet starts the first British legal action against OpenAI, accusing the company of breaching its copyright.",
    "Press Release(s)": "['https://www.thetimes.com/uk/technology-uk/article/mumsnet-openai-sues-copyright-infringement-cz5hzvf8s']"
  },
  {
    "Date": "10/1/2024",
    "Platform": "Perplexity",
    "Partner": "Dow Jones",
    "Deal type": "copyright infringement",
    "Reported Details": "Dow Jones, the parent company of the Wall Street Journal, and the New York Post sue Perplexity for copyright infringement. “This suit is brought by news publishers who seek redress for Perplexity’s brazen scheme to compete for readers while simultaneously freeriding on the valuable content the publishers produce, ” the publishers said in the complaint",
    "Press Release(s)": "['https://www.wsj.com/business/media/wall-street-journal-new-york-post-sue-perplexity-ai-c5d9554d']"
  },
  {
    "Date": "11/1/2024",
    "Platform": "OpenAI",
    "Partner": "ANI, NDTV, Indian Express, Hindustan Times, Digital News Publishers Association",
    "Deal type": "copyright infringement",
    "Reported Details": "In November 2024, Indian news agency Asian News International (ANI) sues OpenAI for unauthorized use of its content. In January 2025, additional Indian news outlets including NDTV, Network18, the Indian Express and the Hindustan Times join ANI's lawsuit against OpenAI for improperly using their copyrighted content. The publishers argue that though OpenAI has entered into partnership agreements with media outlets abroad, it has not entered into similar deals in India, hurting local media companies",
    "Press Release(s)": "['https://www.hindustantimes.com/india-news/news-agency-ani-sues-openai-for-alleged-violation-of-intellectual-property-rights-101731945177550.html, https://www.reuters.com/technology/openai-face-indian-digital-news-firms-ambani-adani-copyright-battle-2025-01-27/']"
  },
  {
    "Date": "11/1/2024",
    "Platform": "OpenAI",
    "Partner": "Toronto Star, Metroland Media, Postmedia, The Globe and Mail, The Canadian Press, CBC",
    "Deal type": "copyright infringement",
    "Reported Details": "A broad coalition of major Canadian news organizations - including the Toronto Star, Metroland Media, Postmedia, The Globe and Mail, The Canadian Press and CBC - sues OpenAI, alleging the AI company is illegally using news articles to train ChatGPT. This marks the first time all of a country's major publishers have come together in litigation against the AI company. The suit seeks punitive damages, disgorgement of any profits made by OpenAI from using the news organizations’ articles, and an injunction barring OpenAI from using any of the news articles in the future",
    "Press Release(s)": "['https://www.toronto.com/news/business/canada-s-major-news-organizations-band-together-to-sue-chatgpt-creator-openai/article_68f6a297-b454-5106-b2de-226cbc2fb1b6.html']"
  },
  {
    "Date": "2/1/2025",
    "Platform": "Cohere",
    "Partner": "News/Media Alliance",
    "Deal type": "copyright infringement, trademark infringement",
    "Reported Details": "A collection of news and media publishers sue AI startup Cohere for copyright and trademark infringement. They accuse the company of improperly using at least 4,000 copyrighted works to train its large language model and of displaying large portions of or entire articles for users while bypassing visits to the publishers' websites",
    "Press Release(s)": "['https://www.wsj.com/business/media/conde-nast-mcclatchy-and-other-publishers-accuse-ai-firm-cohere-of-copyright-violations-5f5ceaff']"
  },
  {
    "Date": "4/1/2025",
    "Platform": "OpenAI",
    "Partner": "Ziff Davis",
    "Deal type": "copyright infringement",
    "Reported Details": "Ziff Davis, a publisher with more than 45 global websites, sues OpenAI for “intentionally and relentlessly reproduc[ing] exact copies and created derivatives\" of its works, infringing on its copyrights and diluting its trademarks. The Ziff Davis also alleges OpenAI trained its AI models on its work even the publisher blocked the company's web crawlers. The publisher seeks at least hundreds of millions of dollars in damages.",
    "Press Release(s)": "['https://www.nytimes.com/2025/04/24/business/media/ziff-davis-openai-lawsuit.html']"
  }
],
    Licensing: [
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "AWP Finanznachrichten AG",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "Barron's",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "Dow Jones Newswires",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "Financial News",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "Investor's Business Daily",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "MarketWatch",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "News Corp Australia",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "News UK",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "Private Equity News",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "The Associated Press",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "The Wall Street Journal",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "11/13/2024",
    "Platform": "Factiva/Dow Jones",
    "Partner": "The Washington Post",
    "Deal type": "Licensing",
    "Reported Details": "Dow Jones is building the world's premiere collection of full-text news articles permissioned for use with GenAI tools and applications, with licensing agreements spanning nearly 4,000 sources, 160+ countries and 29 languages\" (webull.com).",
    "Press Release(s)": "['https://www.dowjones.com/press-room/dow-jones-launches-factiva-smart-summary/']"
  },
  {
    "Date": "10/25/2024",
    "Platform": "Meta",
    "Partner": "Reuters",
    "Deal type": "Licensing",
    "Reported Details": "Neither Meta, nor Reuters-parent Thomson Reuters, disclosed the financial details of the partnership.\" (reuters.com).",
    "Press Release(s)": "https://www.axios.com/2024/10/25/meta-reuters-ai-news-facebook-instagram"
  },
  {
    "Date": "4/29/2024",
    "Platform": "Microsoft",
    "Partner": "Axel Springer",
    "Deal type": "Licensing",
    "Reported Details": "",
    "Press Release(s)": "['https://www.axelspringer.com/en/ax-press-release/axel-springer-and-microsoft-expand-partnership-across-advertising-ai-content-and-azure-services', 'https://openai.com/index/axel-springer-partnership/']"
  },
  {
    "Date": "5/8/2024",
    "Platform": "Microsoft",
    "Partner": "Informa",
    "Deal type": "Licensing",
    "Reported Details": "The agreement includes payment to Informa of both an initial data access fee ($10m+) and a recurring payment across three years (2025, 2026, 2027)\" (informa.com).\"Informa, the UK publishing and exhibitions company, has struck a deal with Microsoft worth more than $10mn in its first year to give access to its data and improve the US technology group’s artificial intelligence systems\" (ft.com).",
    "Press Release(s)": "['https://www.informa.com/globalassets/documents/investor-relations/2024/informa-plc---market-update.pdf']"
  },
  {
    "Date": "10/1/2024",
    "Platform": "Microsoft",
    "Partner": "Axel Springer",
    "Deal type": "Licensing",
    "Reported Details": "All read in your favorite Copilot Voice... Copilot Daily will only pull from authorized content sources\" (blogs.microsoft.com).\"Microsoft won’t reveal how much it’s paying publishers, nor the other terms of the arrangements, but the company did say it plans to add publishers and expand Copilot Daily to new countries 'soon.'\" (techcrunch.com).",
    "Press Release(s)": "['https://blogs.microsoft.com/blog/2024/10/01/an-ai-companion-for-everyone/']"
  },
  {
    "Date": "10/1/2024",
    "Platform": "Microsoft",
    "Partner": "Hearst Magazines",
    "Deal type": "Licensing",
    "Reported Details": "All read in your favorite Copilot Voice... Copilot Daily will only pull from authorized content sources\" (blogs.microsoft.com).\"Microsoft won’t reveal how much it’s paying publishers, nor the other terms of the arrangements, but the company did say it plans to add publishers and expand Copilot Daily to new countries 'soon.'\" (techcrunch.com).",
    "Press Release(s)": "['https://blogs.microsoft.com/blog/2024/10/01/an-ai-companion-for-everyone/']"
  },
  {
    "Date": "10/1/2024",
    "Platform": "Microsoft",
    "Partner": "Reuters",
    "Deal type": "Licensing",
    "Reported Details": "All read in your favorite Copilot Voice... Copilot Daily will only pull from authorized content sources\" (blogs.microsoft.com).\"Microsoft won’t reveal how much it’s paying publishers, nor the other terms of the arrangements, but the company did say it plans to add publishers and expand Copilot Daily to new countries 'soon.'\" (techcrunch.com).",
    "Press Release(s)": "['https://blogs.microsoft.com/blog/2024/10/01/an-ai-companion-for-everyone/']"
  },
  {
    "Date": "10/1/2024",
    "Platform": "Microsoft",
    "Partner": "The Financial Times",
    "Deal type": "Licensing",
    "Reported Details": "All read in your favorite Copilot Voice... Copilot Daily will only pull from authorized content sources\" (blogs.microsoft.com).\"Microsoft won’t reveal how much it’s paying publishers, nor the other terms of the arrangements, but the company did say it plans to add publishers and expand Copilot Daily to new countries 'soon.'\" (techcrunch.com).",
    "Press Release(s)": "['https://blogs.microsoft.com/blog/2024/10/01/an-ai-companion-for-everyone/']"
  },
  {
    "Date": "10/1/2024",
    "Platform": "Microsoft",
    "Partner": "USA Today Network",
    "Deal type": "Licensing",
    "Reported Details": "All read in your favorite Copilot Voice... Copilot Daily will only pull from authorized content sources\" (blogs.microsoft.com).\"Microsoft won’t reveal how much it’s paying publishers, nor the other terms of the arrangements, but the company did say it plans to add publishers and expand Copilot Daily to new countries 'soon.'\" (techcrunch.com).",
    "Press Release(s)": "['https://blogs.microsoft.com/blog/2024/10/01/an-ai-companion-for-everyone/']"
  },
  {
    "Date": "3/12/2023",
    "Platform": "NVidia",
    "Partner": "Getty Images",
    "Deal type": "Licensing",
    "Reported Details": "",
    "Press Release(s)": "['https://blogs.nvidia.com/blog/generative-ai-getty-images/']"
  },
  {
    "Date": "7/13/2023",
    "Platform": "OpenAI",
    "Partner": "Associated Press",
    "Deal type": "Licensing",
    "Reported Details": "The AP’s deal, in the single-digit millions a year, is more narrowly focused on the use of text archives for training\" (wsj.com).",
    "Press Release(s)": "['https://www.ap.org/media-center/press-releases/2023/ap-open-ai-agree-to-share-select-news-content-and-technology-in-new-collaboration/']"
  },
  {
    "Date": "12/13/2023",
    "Platform": "OpenAI",
    "Partner": "Axel Springer",
    "Deal type": "Licensing",
    "Reported Details": "Among the other publishing deals OpenAI has done, Axel Springer’s three-year pact, which includes use of its content for both training and display, is worth at least $25 million to $30 million over three years, according to people familiar with the deals\" (wsj.com).\"The deal, which includes a 'performance fee' based on how much OpenAI uses its content, is worth more than $10 million per year, a person familiar with the agreement said\" (nytimes.com).",
    "Press Release(s)": "['https://openai.com/blog/axel-springer-partnership']"
  },
  {
    "Date": "3/13/2024",
    "Platform": "OpenAI",
    "Partner": "Le Monde",
    "Deal type": "Licensing",
    "Reported Details": "",
    "Press Release(s)": "['https://www.lemonde.fr/en/about-us/article/2024/03/13/le-monde-signs-artificial-intelligence-partnership-agreement-with-open-ai_6615418_115.html', 'https://openai.com/index/global-news-partnerships-le-monde-and-prisa-media/']"
  },
  {
    "Date": "3/13/2024",
    "Platform": "OpenAI",
    "Partner": "Prisa Media",
    "Deal type": "Licensing",
    "Reported Details": "",
    "Press Release(s)": "['https://www.prisa.com/es/noticias/noticias-1/openai-anuncia-un-acuerdo-con-prisa-media-y-le-monde', 'https://openai.com/index/global-news-partnerships-le-monde-and-prisa-media/']"
  },
  {
    "Date": "4/29/2024",
    "Platform": "OpenAI",
    "Partner": "The Financial Times",
    "Deal type": "Licensing",
    "Reported Details": "The FT, whose deal also includes both display and training, is worth $5 million to $10 million a year, according to a person familiar with the matter\" (wsj.com).\"It is the fifth such deal to be struck by OpenAI over the past year... Financial terms were not disclosed\" (ft.com).",
    "Press Release(s)": "['https://aboutus.ft.com/press_release/openai?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-8LNS8DF2FAurlzNv-TFTZKbJ0jKgiLC0wmKt8MgCKBZQFvWmuJJuwXqSWNb-qAt3KNkO8m', 'https://openai.com/index/content-partnership-with-financial-times/']"
  },
  {
    "Date": "5/7/2024",
    "Platform": "OpenAI",
    "Partner": "Dotdash Meredith",
    "Deal type": "Licensing",
    "Reported Details": "",
    "Press Release(s)": "['https://www.prnewswire.com/news-releases/dotdash-meredith-announces-strategic-partnership-with-openai-bringing-iconic-brands-and-trusted-content-to-chatgpt-302138231.html']"
  },
  {
    "Date": "5/22/2024",
    "Platform": "OpenAI",
    "Partner": "News Corp",
    "Deal type": "Licensing",
    "Reported Details": "The deal could be worth more than $250 million over five years, including compensation in the form of cash and credits for use of OpenAI technology, according to people familiar with the situation\" (wsj.com).",
    "Press Release(s)": "['https://newscorp.com/2024/05/22/news-corp-and-openai-sign-landmark-multi-year-global-partnership/', 'https://openai.com/index/news-corp-and-openai-sign-landmark-multi-year-global-partnership/']"
  },
  {
    "Date": "5/29/2024",
    "Platform": "OpenAI",
    "Partner": "The Atlantic",
    "Deal type": "Licensing",
    "Reported Details": "As part of the deals, OpenAI will be able to display news from The Atlantic and Vox Media — which owns The Verge and New York Magazine, among other news outlets — in products like ChatGPT. The startup can also use the publishers’ content to train its AI models. Financial terms of the deals weren’t disclosed\" (bloomberg.com).",
    "Press Release(s)": "['https://www.theatlantic.com/press-releases/archive/2024/05/atlantic-product-content-partnership-openai/678529/', 'https://openai.com/index/enhancing-news-in-chatgpt-with-the-atlantic/']"
  },
  {
    "Date": "5/29/2024",
    "Platform": "OpenAI",
    "Partner": "Vox Media",
    "Deal type": "Licensing",
    "Reported Details": "As part of the deals, OpenAI will be able to display news from The Atlantic and Vox Media — which owns The Verge and New York Magazine, among other news outlets — in products like ChatGPT. The startup can also use the publishers’ content to train its AI models. Financial terms of the deals weren’t disclosed\" (bloomberg.com).",
    "Press Release(s)": "['https://www.voxmedia.com/2024/5/29/24166483/vox-media-openai-strategic-content-and-product-partnership', 'https://openai.com/index/a-content-and-product-partnership-with-vox-media/']"
  },
  {
    "Date": "6/27/2024",
    "Platform": "OpenAI",
    "Partner": "TIME",
    "Deal type": "Licensing",
    "Reported Details": "Financial terms weren't disclosed, but previous deals that OpenAI has struck have been structured to include compensation for publishers.\" (axios.com).",
    "Press Release(s)": "['https://time.com/6992955/time-and-openai-announce-strategic-content-partnership/', 'https://openai.com/index/strategic-content-partnership-with-time/']"
  },
  {
    "Date": "8/20/2024",
    "Platform": "OpenAI",
    "Partner": "Conde Nast",
    "Deal type": "Licensing",
    "Reported Details": "OpenAI's statement suggests the deal with Condé Nast is similar in structure to the search deals struck with The Atlantic and News Corp.\" (axios.com).\"It’s crucial that we meet audiences where they are and embrace new technologies while also ensuring proper attribution and compensation for use of our intellectual property.\" (condenast.com).",
    "Press Release(s)": "['https://www.condenast.com/news/conde-nast-openai-partnership', 'https://openai.com/index/conde-nast/']"
  },
  {
    "Date": "10/8/2024",
    "Platform": "OpenAI",
    "Partner": "Hearst",
    "Deal type": "Licensing",
    "Reported Details": "It's safe to assume Hearst is being compensated millions for its intellectual property, in addition to credits. OpenAI confirmed it will extend credits for Hearst to leverage its AI technology.\" (axios.com).",
    "Press Release(s)": "['https://www.hearst.com/-/hearst-and-openai-announce-strategic-content-partnership', 'https://openai.com/index/hearst/']"
  },
  {
    "Date": "12/4/2024",
    "Platform": "OpenAI",
    "Partner": "Future",
    "Deal type": "Licensing",
    "Reported Details": "",
    "Press Release(s)": "['https://openai.com/index/openai-and-future-partner-on-specialist-content/']"
  },
  {
    "Date": "1/15/2025",
    "Platform": "OpenAI",
    "Partner": "Axios",
    "Deal type": "Licensing",
    "Reported Details": "OpenAI will fund Axios' expansion into Pittsburgh; Kansas City, Missouri; Boulder, Colorado; and Huntsville, Alabama, the companies said. ChatGPT will use Axios journalism to answer user queries with attributed summaries, quotes and links to Axios stories. Axios can access OpenAI's technology to build its own AI products, processes, and systems.\" (axios.com).",
    "Press Release(s)": "['https://www.axios.com/2025/01/15/axios-openai-go-big-in-local', 'https://openai.com/index/partnering-with-axios-expands-openai-work-with-the-news-industry/']"
  },
  {
    "Date": "2/10/2025",
    "Platform": "OpenAI",
    "Partner": "Schibsted Media Group",
    "Deal type": "Licensing",
    "Reported Details": "The partnership will mean OpenAI can integrate real-time news articles from a selection of Schibsted Media’s brands, such as VG, Aftenposten, Aftonbladet, and Svenska Dagbladet, into OpenAI’s products, including ChatGPT. \" (schibstedmedia.com).",
    "Press Release(s)": "['https://schibstedmedia.com/news/schibsted-media-partners-with-openai/', 'https://openai.com/index/openai-partners-with-schibsted-media-group/']"
  },
  {
    "Date": "2/19/2025",
    "Platform": "OpenAI",
    "Partner": "Guardian Media Group",
    "Deal type": "Licensing",
    "Reported Details": "Under the partnership, Guardian reporting and archive journalism will be available as a news source within ChatGPT, alongside the publication of attributed short summaries and article extracts. In addition, the Guardian will also roll out ChatGPT Enterprise to develop new products, features and tools.\" (theguardian.com).",
    "Press Release(s)": "['https://www.theguardian.com/gnm-press-office/2025/feb/14/guardian-media-group-announces-strategic-partnership-with-openai', 'https://openai.com/index/openai-and-guardian-media-group-launch-content-partnership/']"
  },
  {
    "Date": "7/29/2024",
    "Platform": "Perplexity",
    "Partner": "Der Spiegel",
    "Deal type": "Licensing",
    "Reported Details": "the revenue share is a multiyear agreement with a 'double-digit percentage,' consistent across all publishers, with especially favorable terms for the initial partners.\" (theverge.com).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/introducing-the-perplexity-publishers-program']"
  },
  {
    "Date": "7/29/2024",
    "Platform": "Perplexity",
    "Partner": "Entrepreneur",
    "Deal type": "Licensing",
    "Reported Details": "the revenue share is a multiyear agreement with a 'double-digit percentage,' consistent across all publishers, with especially favorable terms for the initial partners.\" (theverge.com).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/introducing-the-perplexity-publishers-program']"
  },
  {
    "Date": "7/29/2024",
    "Platform": "Perplexity",
    "Partner": "Fortune",
    "Deal type": "Licensing",
    "Reported Details": "the revenue share is a multiyear agreement with a 'double-digit percentage,' consistent across all publishers, with especially favorable terms for the initial partners.\" (theverge.com).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/introducing-the-perplexity-publishers-program']"
  },
  {
    "Date": "7/29/2024",
    "Platform": "Perplexity",
    "Partner": "TIME",
    "Deal type": "Licensing",
    "Reported Details": "the revenue share is a multiyear agreement with a 'double-digit percentage,' consistent across all publishers, with especially favorable terms for the initial partners.\" (theverge.com).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/introducing-the-perplexity-publishers-program']"
  },
  {
    "Date": "7/29/2024",
    "Platform": "Perplexity",
    "Partner": "The Texas Tribune",
    "Deal type": "Licensing",
    "Reported Details": "the revenue share is a multiyear agreement with a 'double-digit percentage,' consistent across all publishers, with especially favorable terms for the initial partners.\" (theverge.com).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/introducing-the-perplexity-publishers-program']"
  },
  {
    "Date": "7/29/2024",
    "Platform": "Perplexity",
    "Partner": "WordPress.com",
    "Deal type": "Licensing",
    "Reported Details": "the revenue share is a multiyear agreement with a 'double-digit percentage,' consistent across all publishers, with especially favorable terms for the initial partners.\" (theverge.com).",
    "Press Release(s)": "['https://wordpress.com/blog/2024/07/30/perplexity-partnership/', 'https://www.perplexity.ai/hub/blog/introducing-the-perplexity-publishers-program']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Adweek",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Blavity",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "DPReview",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Gear Patrol",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Lee Enterprises",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Los Angeles Times",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "MediaLab",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Mexico News Daily",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Minkabu Infonoid",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "NTV",
    "Partner": "Reuters",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "NewsPicks",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Prisa Media",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "Stern",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "The Independent",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "12/6/2024",
    "Platform": "Perplexity",
    "Partner": "World History Encyclopedia",
    "Deal type": "Licensing",
    "Reported Details": "As part of the program, these publishers will share in revenue generated from advertising. They’ll also have access to our APIs and developer support to build unique features using our proprietary search technology. They will receive free Perplexity Enterprise Pro for their entire organization for a year. Additionally, they’ll receive data analytics to help track trends and content performance as long as they remain in the program.\" (perplexity.ai).",
    "Press Release(s)": "['https://www.perplexity.ai/hub/blog/perplexity-expands-publisher-program-with-15-new-media-partners']"
  },
  {
    "Date": "8/7/2024",
    "Platform": "ProRata",
    "Partner": "Axel Springer",
    "Deal type": "Licensing",
    "Reported Details": "Prorata is planning to launch its own chatbot in the autumn and will share half the revenue from subscriptions with its licensing partners.\" (pressgazette.co.uk).",
    "Press Release(s)": "['https://www.prorata.ai/']"
  },
  {
    "Date": "8/7/2024",
    "Platform": "ProRata",
    "Partner": "Fortune",
    "Deal type": "Licensing",
    "Reported Details": "Prorata is planning to launch its own chatbot in the autumn and will share half the revenue from subscriptions with its licensing partners.\" (pressgazette.co.uk).",
    "Press Release(s)": "['https://www.prorata.ai/']"
  },
  {
    "Date": "8/7/2024",
    "Platform": "ProRata",
    "Partner": "The Atlantic",
    "Deal type": "Licensing",
    "Reported Details": "Prorata is planning to launch its own chatbot in the autumn and will share half the revenue from subscriptions with its licensing partners.\" (pressgazette.co.uk).",
    "Press Release(s)": "['https://www.prorata.ai/']"
  },
  {
    "Date": "8/7/2024",
    "Platform": "ProRata",
    "Partner": "The Financial Times",
    "Deal type": "Licensing",
    "Reported Details": "Prorata is planning to launch its own chatbot in the autumn and will share half the revenue from subscriptions with its licensing partners.\" (pressgazette.co.uk).",
    "Press Release(s)": "['https://www.prorata.ai/']"
  },
  {
    "Date": "8/7/2024",
    "Platform": "ProRata",
    "Partner": "Universal Music Group",
    "Deal type": "Licensing",
    "Reported Details": "Prorata is planning to launch its own chatbot in the autumn and will share half the revenue from subscriptions with its licensing partners.\" (pressgazette.co.uk).",
    "Press Release(s)": "['https://www.prorata.ai/']"
  },
  {
    "Date": "9/27/2024",
    "Platform": "ProRata",
    "Partner": "TIME",
    "Deal type": "Licensing",
    "Reported Details": "ProRata.ai is still figuring out how it’s going to make money, meaning publishers partnering with the company are committing to a vision, not a proof of concept.\" (digiday.com).",
    "Press Release(s)": ""
  },
  {
    "Date": "11/20/2024",
    "Platform": "ProRata",
    "Partner": "Exponential View",
    "Deal type": "Licensing",
    "Reported Details": "Half of ProRata.ai's monthly subscription revenue from its search chatbot app upon launch will be divided among all of its media partners... Content partners are compensated based on the percentage of outputs attributed to their work.\" (axios.com).\"ProRata’s technology analyses AI output, measures the value of contributing content and calculates proportional compensation. ProRata has submitted patents for its tech that are awaiting approval.\" (ft.com).",
    "Press Release(s)": "['https://www.businesswire.com/news/home/20241119176784/en/Major-UK-Media-Organizations-Join-ProRata%E2%80%99s-Movement-to-Credit-and-Compensate-Content-Owners-in-the-Age-of-Generative-AI']"
  },
  {
    "Date": "11/20/2024",
    "Platform": "ProRata",
    "Partner": "Guardian Media Group",
    "Deal type": "Licensing",
    "Reported Details": "Half of ProRata.ai's monthly subscription revenue from its search chatbot app upon launch will be divided among all of its media partners... Content partners are compensated based on the percentage of outputs attributed to their work.\" (axios.com).\"ProRata’s technology analyses AI output, measures the value of contributing content and calculates proportional compensation. ProRata has submitted patents for its tech that are awaiting approval.\" (ft.com).",
    "Press Release(s)": "['https://www.businesswire.com/news/home/20241119176784/en/Major-UK-Media-Organizations-Join-ProRata%E2%80%99s-Movement-to-Credit-and-Compensate-Content-Owners-in-the-Age-of-Generative-AI']"
  },
  {
    "Date": "11/20/2024",
    "Platform": "ProRata",
    "Partner": "Hello!",
    "Deal type": "Licensing",
    "Reported Details": "Half of ProRata.ai's monthly subscription revenue from its search chatbot app upon launch will be divided among all of its media partners... Content partners are compensated based on the percentage of outputs attributed to their work.\" (axios.com).\"ProRata’s technology analyses AI output, measures the value of contributing content and calculates proportional compensation. ProRata has submitted patents for its tech that are awaiting approval.\" (ft.com).",
    "Press Release(s)": "['https://www.hellomagazine.com/news/731472/hello-and-prorataai-join-forces-to-revolutionize-ai-content-compensation/', 'https://www.businesswire.com/news/home/20241119176784/en/Major-UK-Media-Organizations-Join-ProRata%E2%80%99s-Movement-to-Credit-and-Compensate-Content-Owners-in-the-Age-of-Generative-AI']"
  },
  {
    "Date": "11/20/2024",
    "Platform": "ProRata",
    "Partner": "Mediahuis",
    "Deal type": "Licensing",
    "Reported Details": "Half of ProRata.ai's monthly subscription revenue from its search chatbot app upon launch will be divided among all of its media partners... Content partners are compensated based on the percentage of outputs attributed to their work.\" (axios.com).\"ProRata’s technology analyses AI output, measures the value of contributing content and calculates proportional compensation. ProRata has submitted patents for its tech that are awaiting approval.\" (ft.com).",
    "Press Release(s)": "['https://www.businesswire.com/news/home/20241119176784/en/Major-UK-Media-Organizations-Join-ProRata%E2%80%99s-Movement-to-Credit-and-Compensate-Content-Owners-in-the-Age-of-Generative-AI']"
  },
  {
    "Date": "11/20/2024",
    "Platform": "ProRata",
    "Partner": "Prospect",
    "Deal type": "Licensing",
    "Reported Details": "Half of ProRata.ai's monthly subscription revenue from its search chatbot app upon launch will be divided among all of its media partners... Content partners are compensated based on the percentage of outputs attributed to their work.\" (axios.com).\"ProRata’s technology analyses AI output, measures the value of contributing content and calculates proportional compensation. ProRata has submitted patents for its tech that are awaiting approval.\" (ft.com).",
    "Press Release(s)": "['https://www.businesswire.com/news/home/20241119176784/en/Major-UK-Media-Organizations-Join-ProRata%E2%80%99s-Movement-to-Credit-and-Compensate-Content-Owners-in-the-Age-of-Generative-AI']"
  },
  {
    "Date": "11/20/2024",
    "Platform": "ProRata",
    "Partner": "Reach PLC",
    "Deal type": "Licensing",
    "Reported Details": "Half of ProRata.ai's monthly subscription revenue from its search chatbot app upon launch will be divided among all of its media partners... Content partners are compensated based on the percentage of outputs attributed to their work.\" (axios.com).\"ProRata’s technology analyses AI output, measures the value of contributing content and calculates proportional compensation. ProRata has submitted patents for its tech that are awaiting approval.\" (ft.com).",
    "Press Release(s)": "['https://www.businesswire.com/news/home/20241119176784/en/Major-UK-Media-Organizations-Join-ProRata%E2%80%99s-Movement-to-Credit-and-Compensate-Content-Owners-in-the-Age-of-Generative-AI']"
  },
  {
    "Date": "11/20/2024",
    "Platform": "ProRata",
    "Partner": "Sky News",
    "Deal type": "Licensing",
    "Reported Details": "Half of ProRata.ai's monthly subscription revenue from its search chatbot app upon launch will be divided among all of its media partners... Content partners are compensated based on the percentage of outputs attributed to their work.\" (axios.com).\"ProRata’s technology analyses AI output, measures the value of contributing content and calculates proportional compensation. ProRata has submitted patents for its tech that are awaiting approval.\" (ft.com).",
    "Press Release(s)": "['https://www.businesswire.com/news/home/20241119176784/en/Major-UK-Media-Organizations-Join-ProRata%E2%80%99s-Movement-to-Credit-and-Compensate-Content-Owners-in-the-Age-of-Generative-AI']"
  },
  {
    "Date": "11/20/2024",
    "Platform": "ProRata",
    "Partner": "dmg media",
    "Deal type": "Licensing",
    "Reported Details": "Half of ProRata.ai's monthly subscription revenue from its search chatbot app upon launch will be divided among all of its media partners... Content partners are compensated based on the percentage of outputs attributed to their work.\" (axios.com).\"ProRata’s technology analyses AI output, measures the value of contributing content and calculates proportional compensation. ProRata has submitted patents for its tech that are awaiting approval.\" (ft.com).",
    "Press Release(s)": "['https://www.dmgmedia.co.uk/news/dmg-media-makes-first-generative-ai-investment/', 'https://www.businesswire.com/news/home/20241119176784/en/Major-UK-Media-Organizations-Join-ProRata%E2%80%99s-Movement-to-Credit-and-Compensate-Content-Owners-in-the-Age-of-Generative-AI']"
  }
],
    'Other Deals': [
  {
    "Date": "5/29/2024",
    "Platform": "OpenAI",
    "Partner": "WAN-IFRA",
    "Deal type": "Accelerator Program",
    "Reported Details": "",
    "Press Release(s)": "['https://wan-ifra.org/2024/05/wan-ifra-and-openai-launch-global-ai-accelerator-for-newsrooms/', 'https://openai.com/index/newsroom-ai-catalyst-global-program-with-wan-ifra/']"
  },
  {
    "Date": "2/5/2024",
    "Platform": "Microsoft",
    "Partner": "Semafor",
    "Deal type": "Curation Tool",
    "Reported Details": "As part of the agreement, Microsoft is paying an undisclosed sum of money to Semafor to sponsor a breaking news feed called 'Signals'. The companies would not share financial details, but the amount of money is 'substantial' to Semafor’s business, said a person familiar with the matter.\" (ft.com).",
    "Press Release(s)": "['https://www.semafor.com/article/02/05/2024/introducing-semafor-signals', 'https://blogs.microsoft.com/on-the-issues/2024/02/05/journalism-news-generative-ai-democracy-forward/']"
  },
  {
    "Date": "10/22/2024",
    "Platform": "OpenAI",
    "Partner": "The Lenfest Institute for Journalism",
    "Deal type": "Grantmaking",
    "Reported Details": "OpenAI and Microsoft are each awarding $2.5 million in direct funding and $2.5 million in software and enterprise credits, for a total of up to $10 million.\" (lenfestinstitute.org).In the initial round of funding, Chicago Public Media, Newsday (Long Island, NY), The Minnesota Star Tribune, The Philadelphia Inquirer, and The Seattle Times will each receive a grant to hire a two-year \"AI fellow to pursue projects that focus largely on improving business sustainability and implementing AI technologies within their organizations. The fellowship will also provide OpenAI and Microsoft Azure credits to help these publications experiment and develop tools to assist with local news.\" (lenfestinstitute.org).",
    "Press Release(s)": "['https://www.lenfestinstitute.org/institute-news/lenfest-institute-openai-microsoft-ai-collaborative-fellowship/', 'https://openai.com/index/lenfest-institute/']"
  },
  {
    "Date": "7/18/2023",
    "Platform": "OpenAI",
    "Partner": "American Journalism Project",
    "Deal type": "Grantmaking",
    "Reported Details": "OpenAI is committing $5 million to the American Journalism Project to support the expansion of AJP’s work and up to $5 million in OpenAI API credits to help its grantee organizations assess and deploy emerging AI technologies within their organizations\" (theajp.org).",
    "Press Release(s)": "['https://www.theajp.org/news-insights/announcements/american-journalism-project-announces-new-partnership-with-openai-to-support-local-news/', 'https://openai.com/index/partnership-with-american-journalism-project-to-support-local-news/']"
  },
  {
    "Date": "10/22/2024",
    "Platform": "OpenAI",
    "Partner": "Chicago Public Media",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "Five metro outlets... will each receive $500,000 to hire a two-year “AI fellow” to develop AI projects, plus software and enterprise credits.\" (seattletimes.com).\"Chicago Public Media, which publishes The Chicago Sun-Times and runs public radio station WBEZ, will focus on leveraging AI for transcription, summarization and translation to expand content offerings and reach new audiences. \" (lenfestinstitute.org).",
    "Press Release(s)": "['https://openai.com/index/lenfest-institute/']"
  },
  {
    "Date": "10/22/2024",
    "Platform": "OpenAI",
    "Partner": "Newsday (Long Island, NY)",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "Newsday Media Group has been chosen for a $500,000 grant to develop an artificial intelligence tool that will enable its journalists, readers and businesses to access and analyze data about Long Island.\" (newsday.com).\"Newsday will build AI public data summarization and aggregation tools for its newsroom, for readers and for businesses as a marketing services offering.\" (lenfestinstitute.org).",
    "Press Release(s)": "['https://openai.com/index/lenfest-institute/']"
  },
  {
    "Date": "10/22/2024",
    "Platform": "OpenAI",
    "Partner": "The Minnesota Star Tribune",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "Five metro outlets... will each receive $500,000 to hire a two-year “AI fellow” to develop AI projects, plus software and enterprise credits.\" (seattletimes.com).\"The Minnesota Star Tribune will experiment with AI summarization, analysis and content discovery for both its journalists and readers.\" (lenfestinstitute.org).",
    "Press Release(s)": "['https://openai.com/index/lenfest-institute/']"
  },
  {
    "Date": "10/22/2024",
    "Platform": "OpenAI",
    "Partner": "The Philadelphia Inquirer",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "Five metro outlets... will each receive $500,000 to hire a two-year “AI fellow” to develop AI projects, plus software and enterprise credits.\" (seattletimes.com).\"The Philadelphia Inquirer will use AI platforms to build a conversational search interface for its archives. It will also leverage AI to monitor and analyze media produced by local municipalities and agencies.\" (lenfestinstitute.org).",
    "Press Release(s)": "['https://openai.com/index/lenfest-institute/']"
  },
  {
    "Date": "10/22/2024",
    "Platform": "OpenAI",
    "Partner": "The Seattle Times",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "Five metro outlets, including The Seattle Times, will each receive $500,000 to hire a two-year “AI fellow” to develop AI projects, plus software and enterprise credits.\" (seattletimes.com).\"The Seattle Times will use AI platforms to assist in advertising go-to-market, sales training support, and other sales analytics before rolling out learnings to other business functions and departments.\" (lenfestinstitute.org).",
    "Press Release(s)": "['https://openai.com/index/lenfest-institute/']"
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "CT Mirror",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "Centro de Periodismo Investigativo (CPI)",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "Cityside",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "Knoble said the organization is sketching out how to use the $25,000 grant from AJP to help with learning more about donors to boost fundraising\" (sfchronicle.com).\"one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "Civic News Company",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "Montana Free Press",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "Open Campus",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "Outlier Media",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "Sahan Journal",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "Spotlight PA",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "The City",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "The Marshall Project",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "The Nebraska Journalism Trust",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "12/20/2023",
    "Platform": "OpenAI",
    "Partner": "inewsource",
    "Deal type": "Newsroom Experimentation",
    "Reported Details": "one- to two-year grants, ranging from $25,000 to $200,000\" (theajp.org).",
    "Press Release(s)": ""
  },
  {
    "Date": "2/5/2024",
    "Platform": "Microsoft",
    "Partner": "Nota",
    "Deal type": "Tool Development",
    "Reported Details": "",
    "Press Release(s)": "['https://www.heynota.com/microsoft-journalism-hub/', 'https://blogs.microsoft.com/on-the-issues/2024/02/05/journalism-news-generative-ai-democracy-forward/']"
  },
  {
    "Date": "2/5/2024",
    "Platform": "Microsoft",
    "Partner": "Craig Newmark Graduate School of Journalism, CUNY",
    "Deal type": "Training Program",
    "Reported Details": "",
    "Press Release(s)": "['https://www.journalism.cuny.edu/2024/02/unlocking-the-future-of-journalism/', 'https://blogs.microsoft.com/on-the-issues/2024/02/05/journalism-news-generative-ai-democracy-forward/']"
  },
  {
    "Date": "2/5/2024",
    "Platform": "Microsoft",
    "Partner": "Online News Association",
    "Deal type": "Training Program",
    "Reported Details": "",
    "Press Release(s)": "['https://journalists.org/2024/02/05/ona-launches-ai-in-journalism-initiative/', 'https://blogs.microsoft.com/on-the-issues/2024/02/05/journalism-news-generative-ai-democracy-forward/']"
  },
  {
    "Date": "2/5/2024",
    "Platform": "Microsoft",
    "Partner": "The GroundTruth Project",
    "Deal type": "Training Program",
    "Reported Details": "",
    "Press Release(s)": "['https://thegroundtruthproject.org/heres-how-microsoft-is-working-with-journalists-to-create-the-newsrooms-of-the-future-with-ai/', 'https://blogs.microsoft.com/on-the-issues/2024/02/05/journalism-news-generative-ai-democracy-forward/']"
  },
  {
    "Date": "1/1/2024",
    "Platform": "Google",
    "Partner": "FT Strategies, The Financial Times",
    "Deal type": "Training Program",
    "Reported Details": "",
    "Press Release(s)": "['https://24982124.fs1.hubspotusercontent-eu1.net/hubfs/24982124/GNI/FT%20Strategies%20&%20GNI%20AI%20Launchpad%20Explainer%202024.pdf']"
  },
  {
    "Date": "8/8/2023",
    "Platform": "OpenAI",
    "Partner": "Arthur L. Carter Journalism Institute, NYU",
    "Deal type": "Training Program",
    "Reported Details": "The Ethics and Journalism Initiative, backed by a $395,000 grant from OpenAI, will be led by Stephen Adler, who served as editor-in-chief of Reuters from 2011 to 2021.\" (nyu.edu).",
    "Press Release(s)": "['https://www.nyu.edu/about/news-publications/news/2023/august/arthur-l--carter-journalism-institute-launches-ethics-initiative.html']"
  }
]
  };

  $: filteredData = sankeyFilter
    ? datasets[sankeyFilter]
    : [...datasets.Licensing, ...datasets.Lawsuits];

  const sources = Object.keys(datasets);
  let selected = sources[0];
  let data = datasets[selected];
  let query = '';
  let sankeyFilter = null;
  


  const tabColors = {
    Lawsuits: '#d6613b',
    Licensing: '#9aa27d',
    'Other Deals': '#b7d3f3'
  };

  function select(label) {
    selected = label;
    data = datasets[label];
    query = '';
  }

  function handleSankeyLinkClick(link) {
    sankeyFilter = { source: link.source.name, target: link.target.name };

    // Switch tab to match the source (e.g., "Licensing", "Lawsuits", "Other Deals")
    const tab = Object.keys(datasets).find(
      group => group.replace(/s$/, '') === link.source.name
    );
    if (tab) {
      selected = tab;
      data = datasets[tab];
      query = '';
    }
  }

  function clearSankeyFilter() {
    sankeyFilter = null;
    
  }

  $: filtered = data
  .filter(r =>
    (!query || JSON.stringify(r).toLowerCase().includes(query.toLowerCase())) &&
    (!sankeyFilter ||
      (
        (Array.isArray(r.Platform)
        ? r.Platform.includes(sankeyFilter.target)
        : r.Platform.trim() === sankeyFilter.target)
        &&
        Object.keys(datasets).some(
          group => group.replace(/s$/, '') === sankeyFilter.source && datasets[group].includes(r)
        )
      )
    )
  )
  .slice() // make a shallow copy before sorting
  .sort((a, b) => {
    // Parse dates, fallback to 0 if invalid
    const da = Date.parse(a.Date) || 0;
    const db = Date.parse(b.Date) || 0;
    return db - da; // descending (most recent first)
  });
  
  function getDomain(url) {
    const cleanUrl = url.trim().replace(/^(\[|'|")|(\]|'|")$/g, '').replace(/^'/, '').replace(/'$/, '');
    try {
      return {
        cleanUrl,
        domain: new URL(cleanUrl).hostname.replace(/^www\./, '')
      };
    } catch {
      return { cleanUrl, domain: cleanUrl };
    }
  }

</script>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=EB+Garamond:wght@400;600;700&display=swap" rel="stylesheet">

<div
  class="tracker-wrapper"
  style="--accent: {tabColors[selected]};"
>
  <!-- Header -->
<div class="article">
  <div class="header">
    <div class="title-container">
      <div class="title-row">
        <div class="logo">
          <img src="Tow Center Logo.webp" alt="Tow Center Logo" />
        </div>
        <span id="title-style">Tow Center for Digital Journalism's</span>
      </div>
      <h1 class="article-title">AI Deals and Lawsuits Tracker</h1>
    </div>
  </div>

  <p class="article-intro">
    This tracker, compiled by the Tow Center for Digital Journalism as part of the <a href = "https://towcenter.columbia.edu/news/platforms-and-publishers">Platforms and Publishers project</a>, monitors formal developments in the relationship between news publishers and AI companies, including lawsuits, licensing partnerships, and other types of deals.
  </p>

  <p class="article-intro">
    To follow developments between news organizations and technology companies broadly, check out our <a href = "https://tow.cjr.org/platform-timeline/">Platforms and Publishers Timeline</a>.
  </p>

  <p class="article-intro">
    This tracker is currently maintained by <a href = "https://towcenter.columbia.edu/content/klaudia-jazwinska">Klaudia Jaźwińska</a> and is updated at the beginning of each month. We welcome any feedback or suggestions regarding missed developments.  </p>
  
</div>

  <div class="article-footer">

    <p class="update-date">
      
      Last updated: {new Date().toLocaleDateString('en-US', {
        month: 'long',
        day: 'numeric',
        year: 'numeric'
      })}
      
    </p>
  </div>



  <section class="sankey-wrapper">
    <SankeyDiagram
      {datasets}
      width={900}
      height={520}
      onLinkClick={handleSankeyLinkClick}
      {sankeyFilter}
    />
  </section>

  <!-- Controls -->
  <section class="controls">
    <div class="tabs">
      {#each sources as label}
        <button
          class="tab {label === selected ? 'tab--active' : ''}"
          style={label === selected
            ? `background:${tabColors[label]};color:#fff;border-color:${tabColors[label]}`
            : ''}
          on:click={() => select(label)}>{label}</button>
      {/each}
    </div>
    <div class="search">
      <input class="search-input" type="text" bind:value={query} placeholder="Search in {selected}…" />
    </div>
  </section>

  {#if sankeyFilter}
    <button class="clear-filter-btn" on:click={clearSankeyFilter} style="margin-bottom:1rem;">
      Clear Sankey Filter: {sankeyFilter.source} → {sankeyFilter.target}
    </button>
  {/if}

  <!-- Table -->
  <div class="table-wrapper">
    <table class="deals-table">
      <thead>
        <tr>
          <th>Date</th>
          <th>Platform</th>
          <th>Publisher</th>
          <th>Type</th>
          <th class="details-col">Reported Details</th>
          <th>Links</th>
        </tr>
      </thead>
      <tbody>
        {#each filtered as row (row.Date + row.Platform + row.Partner)}
          <tr in:fade={{ duration: 200 }}>
            <td class="mono">
              {#if row.Date}
                {new Date(row.Date).toLocaleString('en-US', { month: 'short', year: 'numeric' })}
              {/if}
            </td>
            <td class="platform">
              {#if Array.isArray(row.Platform)}
                {#each row.Platform as p, i}
                  {p}{#if i < row.Platform.length - 1}<br>{/if}
                {/each}
              {:else}
                {row.Platform}
              {/if}
            </td>
            <td>{row.Partner}</td>
            <td>{row['Deal type']}</td>
            <td class="details">{row['Reported Details']}</td>
            <td class="links">
              {#if row['Press Release(s)']}
                {#each row['Press Release(s)'].split(/[,;]/) as url, i}
                  {#if url.trim()}
                    {#key url}
                      <a
                        href={getDomain(url).cleanUrl}
                        target="_blank"
                        rel="noopener"
                      >{getDomain(url).domain}</a>
                      {#if i < row['Press Release(s)'].split(/[,;]/).length - 1}
                        <br>
                      {/if}
                    {/key}
                  {/if}
                {/each}
              {/if}
            </td>
            
          </tr>
        {/each}
        {#if !filtered.length}
          <tr><td colspan="6" class="no-results">No matching deals.</td></tr>
        {/if}
      </tbody>
    </table>
  </div>
</div>

<style>
  :global(html) { scroll-behavior: smooth; }

  /* Color palette */
  :root {
    --text-main: #43485A;
    --text-light: #666;
    --border: #43485A;
    --bg: #fff;
    --bg-alt: rgba(67, 72, 90, 0.05);
  }
    /* Article Layout */
  .article {
    max-width: 680px;
    margin: 4rem auto;
    padding: 0 1rem;
  }

  .article-title {
    font-family: "Helvetica Neue", sans-serif;
    font-size: 3.4rem;
    line-height: 1.2;
    font-weight: 800;
    margin-bottom: 2rem;
    color: #d6613b;
    text-align: left;
    letter-spacing: -0.02em;
    margin-bottom: 2rem;
  }

  .article-intro {
    font-size: 1.2rem;
    font-weight: 400;
    color: #333;
    margin-bottom: 1.5rem;
    text-align: left;
    line-height: 1.8rem;
  }

  .article-footer {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
    margin: 2rem 0;
    padding-top: 1rem;
    border-top: 1px solid rgba(67, 72, 90, 0.1);
  }

  .sankey-wrapper {
    margin: 0 auto;
    max-width: 900px;
    padding: 0 1rem;
    margin-bottom: 2rem;
  }

  /* Layout wrappers */
  .tracker-wrapper {
    max-width: 900px;
    margin: 3rem auto;
    padding: 0 1rem 4rem;
    font-family: "EB Garamond", serif;
    color: var(--text-main);
  }

  /* Tabs */
  .controls {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    align-items: center;
    margin-bottom: 1.5rem;
  }

  .tabs {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
  }
  .tab {
    font-family: "Helvetica Neue", sans-serif;
    font-size: 0.8rem;
    font-weight: 600;
    border: 1px solid var(--border);
    background: var(--bg);
    color: var(--text-main);
    padding: 0.4rem 0.9rem;
    cursor: pointer;
    transition: background-color 0.2s ease, color 0.2s ease;
  }
  .tab:hover { background: var(--bg-alt); }
  .tab--active {
    background: var(--accent);
    color: #fff;
    border-color: var(--accent);
  }

  /* Search */
  .search {
    flex: 1 1 220px;
    position: relative;
  }
  .search-input {
    width: 100%;
    padding: 0.55rem 0.75rem;
    font-family: "Helvetica Neue", sans-serif;
    font-size: 0.85rem;
    border: 1px solid var(--border);
    color: var(--text-main);
    background: var(--bg);
    outline: none;
  }
  .search-input:focus { box-shadow: 0 0 0 2px var(--accent); }

  /* Table */
  .table-wrapper {
    overflow-x: auto;
    border: 1px solid var(--border);
    box-shadow: 4px 4px 0 0 var(--accent);
    
  }

  .deals-table th:first-child,
  .deals-table td.mono {
    width: 5.5rem; 
    min-width: 5.5rem;
  }
  .deals-table {
    width: 100%;
    border-collapse: collapse;
    font-family: "Helvetica Neue", sans-serif;
    font-size: 0.875rem;
  }
  thead {
    background: var(--bg);
    position: sticky;
    top: 0;
    z-index: 5;
  }
  th, td {
    padding: 0.75rem 0.75rem;
    border-bottom: 1px solid rgba(67, 72, 90, 0.2);
    text-align: left;
    vertical-align: top;
  }
  th { font-weight: 700; font-size: 0.75rem; text-transform: uppercase; }

  tbody tr:nth-child(even) { background: var(--bg-alt); }
  tbody tr:hover { background: color-mix(in srgb, var(--accent) 12%, #fff); }

  .mono { font-family: monospace; font-size: 0.8rem; }
  .platform { font-weight: 600; }
  /* .details-col { min-width: 320px;} */
  .details {
    max-width: 40rem;
    line-height: 1.4;

  }
  .links a {
    color: var(--accent);
    text-decoration: none;
    font-weight: 600;
  }
  .links a:hover { text-decoration: underline; }

  .no-results {
    text-align: center;
    padding: 2rem;
    color: var(--text-light);
  }

  /* Responsive */
  @media (max-width: 640px) {
    .details-col { display: none; }
    .details { display: none; }
    th.details-col { display: none; }
  }


  /* Article Layout */
  .article {
    max-width: 680px;
    margin: 4rem auto;
    padding: 0 1rem;
    
  }

  .article-title {
    font-family: "Helvetica Neue", sans-serif;
    font-size: 3.4rem;
    line-height: 1.2;
    font-weight: 800;
    margin-bottom: 2rem;
    color: #d6613b;
    text-align: left;
    letter-spacing: -0.02em;
    margin-bottom: 2rem;
  }

  .article-intro {
    font-size: 1.2rem;
    font-weight: 400;
    color: #333;
    margin-bottom: 1.5rem;
    text-align: left;
    line-height: 1.8rem;
  }

  .search-input {
    width: 100%;
    padding: 0.75rem 3.5rem 0.75rem 1rem; /* extra right padding for button */
    font-size: 0.875rem;
    font-weight: 500;
    border: 1px solid #43485A;
    background: white;
    color: #43485A;
    font-family: 'Helvetica Neue', sans-serif;
    transition: all 0.2s ease;
    box-sizing: border-box;
  }



  /* id title-style */
  #title-style {
    font-family: 'EB Garamond', serif;
    /* italic */
    /* font-style: italic; */
    font-size: 2rem;
    font-weight: 400;
    color: #d6613b;
    text-align: left;
    letter-spacing: 0em;
  }



  @media (max-width: 768px) {
  .article-title {
    font-size: 2rem;
    margin-bottom: 1.5rem;
  }
}


/* a  */

.article-intro a {
    color: #d6613b;
    text-decoration: none;
    font-weight: 600;
  }

  .article-intro a:hover {
    text-decoration: underline;
  }

  /* Add these styles */
  .header {
    margin-bottom: 2rem;
  }

  .title-container {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .title-row {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .logo {
    flex-shrink: 0;
    width: 120px; 
  }

  .clear-filter-btn {
    background: var(--accent, #d6613b);
    color: #fff;
    border: none;
    border-radius: 4px;
    padding: 0.5rem 1.2rem;
    font-size: 1rem;
    font-family: "Helvetica Neue", sans-serif;
    font-weight: 600;
    cursor: pointer;
    margin-bottom: 1rem;
    transition: background 0.2s, color 0.2s, box-shadow 0.2s;
    box-shadow: 0 2px 8px rgba(67,72,90,0.08);
  }
  .clear-filter-btn:hover {
    background: #b94e2c;
    color: #fff;
  }

  .logo img {
    width: 100%;
    height: auto;
  }

  #title-style {
    font-family: 'EB Garamond', serif;
    font-size: 1.5rem;
    font-weight: 400;
    color: #d6613b;
  }

  .article-title {
    font-family: "Helvetica Neue", sans-serif;
    font-size: 3rem;
    line-height: 1.2;
    font-weight: 800;
    color: #d6613b;
    margin: 0;
  }

  /* Responsive adjustments */
  @media (max-width: 768px) {
    .title-row {
      flex-direction: column;
      align-items: flex-start;
      gap: 0.5rem;
    }

    .logo {
      width: 50px;
    }

    #title-style {
      font-size: 1.25rem;
    }

    .article-title {
      font-size: 2rem;
    }
  }


</style>
