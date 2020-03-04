# Docs Search

## Overview
docs.microsoft.com provides a search bar in the universal header that allows user to search the entire docs. After customer enters the search phrase, the ucstomer is taken to a search results page where we display the total number of results and the top ten results. The user can then navigate to other results using the pagination functionality.

> [!IMPORTANT]
> The review site doesn’t have its own search instance. So, the search results are based on what has been published. As a result, if you haven’t published anything with the scope, you won’t see it in the search results. Additionally, there’s a time delay between when a document is published and when it gets indexed by the search service. That can be anywhere between 0 and 30 hours.

## How do we identify what pages need to be crawled?
We use sitemap to identify the urls that need to be crawled so if a page (e.g. old version article) is not part of site map or is marked as NO INDEX NO FOLLOW, it will not be crawled by the docs search engine.

## What do we crawl and index?
[!INCLUDE [searchIndexes](searchIndexes.md)]

## What do we search?
If any content in docs have this search phrase in the (1) title OR (2) description OR (3) body of the article, then the content will be included in the search results. 

> [!IMPORTANT]
> The search phrase is not compared in any other metadata (e.g. keyword).

### How do we order the search results?
[!INCLUDE [search-resultsorder](search-resultsorder.md)]

## Facets
Currently docs search allows user to filter the search results only by scope.   

[!INCLUDE [search-scope](search-scope.md)]



