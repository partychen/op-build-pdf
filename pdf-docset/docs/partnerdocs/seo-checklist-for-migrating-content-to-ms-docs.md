---

# required metadata

title: SEO checklist for content migration to MS Docs | Microsoft Docs
description: The article lists and describes the tasks required to ensure search performance for migrated content to docs.microsoft.com site.
author: khairunj
manager: arthurya
ms.date: 05/26/2017
ms.topic: get-started-article
ms.prod:
ms.service:

---
# SEO checklist for content migration to the Microsoft Docs site

This article provides a checklist of SEO best practices to ensure the search performance of content migrated to the Microsoft Docs site (docs.microsoft.com).

For every migration, there are content and technical SEO tasks that fall into the following categories:
 - Content tasks and requirements
 - Site architecture and technical tasks
 - Tracking migration success - basic metrics

## Why prioritize SEO tasks when you migrate content to a new site?

When you migrate content, there's a high risk of hurting its search performance.

All live webpages and websites collect search performance equity - meaning, Google and Bing have indexed and ranked them, and they have some routine search volume. The longer a page is live and has pageviews, the greater the search performance equity. When you publish a new URL, you start with no search equity.

 In a content migration, you want to transfer the search performance from the old URLs to the new URLs. There is always some temporary loss of search performance - often lasting about a month. But, by following this checklist, you can provide a good customer experience with your migrated content and ensure your content retains its search performance equity.

## Follow URL patterns for products and services

URLs must be consistent, hierarchical, and as shallow as possible in order to perform well in search.

To ensure well-structured URLs, use one of following URL patterns:


    https://docs.microsoft.com/{lang-locale}/{productfamily}/{technology}/{filename}

    https://docs.microsoft.com/{lang-locale}/{productfamily}/{technology}/{userjourney-or-secondary-category}/{filename}
    Use this option if the content set is large and requires deeper hierarchies.

>[!IMPORTANT]

> The more elements (folders) in the URL path, the harder for a search engine to crawl the content. Try to limit URLs to 2-3 levels deep from the base URL https://docs.microsoft.com/{lang-locale}/

## Follow guidance for friendly filenames

The most complete [guidance for friendly filenames](https://github.com/Microsoft/azure-docs/blob/master/contributor-guide/file-names-and-locations.md) is from Azure content. You can adapt it to fit your content set, but the basic friendly URL rules apply:
- Use only lowercase letters, numbers, and hyphens. No other characters are allowed.
- No spaces or punctuation characters. Use the hyphens to separate words and numbers in the file name.
- No more than 80 characters - this is a publishing system limit
- No -ing verbs (gerunds)
- Avoid small words such as a, and, the, in, or, and so on
- All files must be in markdown and use the .md file extension
- Spell the words out; avoid acronyms

### Acronyms and initialisms in filenames
- Spell out service or product names
- Do not use acronyms or abbreviations for products, services, or features.
- You may use industry-standard acronyms or abbreviations, such as DNS or URL. .

### Filename examples
Here are examples of descriptive, relevant file names:
-       machine-learning-interpret-model-results.md
-       install-visual-studio-2015.md   

## Validate SEO metadata

For SEO metadata, refer to  [SEO cheat sheet](https://aka.ms/seo-for-writers-cheat-sheet). It has complete information on metadata that impacts SEO, specifically, the page title and meta description.

- **title**: Title body should be 43 chars or fewer including spaces and use unbranded terms as much as possible in title body. Use product and service brands at the end of the title separated with hyphen.  For more details and examples on title please refer to [title cheat sheet](https://aka.ms/page-title-cheat-sheet). 
- **description**: Even though meta description is not listed as required metadata you should include a brief abstract or description of the content. This meta description usually appears in search engine result page for the topic and helps increase the click through rate.
- Make sure title and description are different. Description should extend on title.
-  **keywords**: Only add keywords that are being tracked for SEO. Google doesn't crawl keywords or use them for search ranking that's why it is not required.

## Ensure landing pages have descriptive content

Each landing page needs a page title, meta description, H1, and on-page text that describes the content set. It's not enough to describe the product or service; you need to use terms that describe the content, so that the page can be found in searches for technical documentation.

If someone searches for *SQL tutorials* or *learn sql database*, they'll only find your documentation landing page if it uses those terms.

### Documentation landing page terms

Examples of documentation landing page terms:
- documentation
- tutorials
- API references (stronger than just "references")
- how-to
- learn
- videos
- walkthroughs

Here's an example of basic [landing page text for Azure SQL Database](https://docs.microsoft.com/en-us/azure/sql-database/):
- **Page title:** SQL Database Documentation | Microsoft Docs
- **Meta description:** Learn SQL Database, a database-as-a-service in the cloud. Tutorials, videos, and other documentation show how to set up, connect, and manage a relational database.
- **H1:** SQL Database Documentation
- **On-page text:** Learn how to use SQL Database, a relational database-as-a-service in the cloud built on the Microsoft SQL Server engine. Tutorials, videos, and other documentation show you how to set up, connect, and manage a SQL database.

## Content quality: Remove duplicate content and low-performing pages

Duplicate content and very low-performing content can hurt the search rank of your content. It's best to remove or edit this content prior to migrating, if you can. Whenever you can do this clean-up, it helps search performance for the content set.

Look for and remove the following:
- Low-performing content: If you have content that consistently gets very low pageviews and search visits, consider removing it and redirecting to other content.
- Duplicate content: Identify duplicate content.
    - Articles that are duplicates or near-duplicates. Make sure each article has a unique intent.
    - Page titles, meta descriptions, and H1s that are identical. Search across reference content, landing pages, and articles to determine whether your content contains duplicate text strings.

## Update high-value links from other sites

Make sure you update high-value links to your content from other sites. You can get a backlinks report (report of links to your content from other sites) from Google Search Console.  

These include:
- Links from internal sites, in the header/footer and in content pages.
- Links from third-party sites that have high authority and influence.

  This task is as hands-on as it sounds. Updating links from third-party sites requires you contact the site owner and make the request. A businesslike, but friendly and appreciative email will generally get results.

## Use 301 redirects
If you move content from MSDN and TechNet to Microsoft Docs, be sure to set up 301 (permanent) redirects. Follow the instructions in [Redirecting MTPS content to Open Publishing Content (OPS)](https://opsdocs.azurewebsites.net/en-us/opsdocs/partnerdocs/paveover-mtps-content?branch=master).
If you move the content within docs site than also setup redirects so that user who has bookmarked the page can get to the content and search juices build for previous topic get's transfer to the new topic URL.
### Why are 301 redirects important?

By using 301 redirects, you ensure that users can find your content - that's the obvious outcome. Redirection also ensures that the new URLs inherit the search authority from the old URLs.

For localized content, submit requests for locale-specific redirection instead of locale-agnostic redirects. This helps transfer the search authority for locales.

## Check for broken links and fix 404s

Broken links and 404s on the site give search engines a negative signal that affects the quality metrics and thus search performance for the entire site. Before your content is merged into the Live branch and released, it's important you run link-checking tools on it. All internal and external links on the page should be fully functional before making the page Live.

OPS build checks for internal links within a repo during build time so make sure to look at the build logs and fix the broken links.

### Repo organization changes and 404s

Your repo folder structure and filenames are part of your URLs. Reorganizing your repo or changing filenames after you release migrated content could result in 404s and broken links, thus hurting the customer experience and the search ranking of your content.

Before you release migrated content, check your repo organization and filenames:
- Will your repo organization scale to the needs of your product or service?
- Do your filenames follow the [established filename guidance](https://github.com/Microsoft/azure-docs/blob/master/contributor-guide/file-names-and-locations.md)?
- Are the resulting URLs as shallow as possible?  

## Enable crawling of newly Published pages

To verify that your new and moved content made to the docs sitemap file you can go to [docs sitemap file](https://docs.microsoft.com/_sitemaps/sitemapindex.xml).  This docs sitemap index file has information for all the sitemaps on the docs site. You should look for your docset and then browse to see the actual URLs are in the sitemap file. 

### Sitemaps
Sitemaps for docs site is an XML file that lists the canonical URLs for the site and shows the structure of the content.  This allows search engine to crawl the site intelligently and provides the information when content was last updated and gives the crawlability and indexing prioritization. 

Sitemaps are generated daily and validation happens at midnight.  So if content is moved from one folder to another or file name changed, resulted in changing the URL, the URL will be listed in sitemap until the next day and will result in 404 for Google and Bing bot.
> [!IMPORTANT]
> It is important for any movements like this, setup appropriate redirects. 

## Track migration with basic metrics

Site metrics can help you identify issues with your migration and show you how your migrated content is performing.

### Search performance metrics
Compare key metrics between the old content URLs and the new content location.

- Search traffic: Pageviews, visits, and visitors from search (Source: aka.ms/skyeye)
- Search page impressions and click-through rate (Source: Google Search Console)
- Page ranking and keyword performance (Source: BrightEdge or similar 3rd-party tool): You can set up dashboards to show how keyword performance and page ranking transfers from one site to another. It takes about 4-5 weeks for the transfer.

### Other useful metrics
You can use other metrics to show performance of migrated content, as well as identify issues.
- Overall traffic and referrers, such as direct traffic, social media referrals, and so on. (aka.ms/skyeye)
- Crawl reports  (Source: Google Webmaster Tools)
