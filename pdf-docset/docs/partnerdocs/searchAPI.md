# Docs Search API

## Objective
The objective of search API is to provide an easy and scalable way to identify the list of technical documentation articles that are relevant to a context or search phrase.

## Potential applications of the API
* The user is on a particular artifact (e.g. page, screen, form etc..) within a product and needs further help on that. So the customer clicks on the help icon or presses a hot key (e.g F1) to get help. The client (i.e. the product) needs a search API that would return documentation results based on the context the user is on. 
* The user opens the help screen and enters free form text to get help results for those search terms. The client (i.e. the product) needs a search API that would return documentation results based on the search terms.
* The user needs help with a functionality so she opens a help ticket. The client (i.e. the product) needs a search API that would return documentation results based on the ticket information.	
* Any combination of the above scenarios.

## API Endpoint
https://docs.microsoft.com/api/search

## API Parameters
### search [Mandatory]
This attribute provides the search phrase that the client wants results on. If any content in docs have this search phrase in the (1) title OR (2) description OR (3) body of the article, then the content will be included in the search results. If * is provided all content will be included in the search results. [Example](https://docs.microsoft.com/api/search?search=General%20ledger&locale=en-us)

> [!IMPORTANT]
> The search phrase is not compared with any other metadata (e.g. keyword).

### locale [Mandatory]
This attribute will be used to get the locale preference for the customer. The searching will be done on all languages in the fallback language chain. If the content is available in the preferred language, we will  include the content in the preferred language.  If the content is not available in the preferred language(s), we will use the fallback behavior to determine the content to be included. [Example](https://docs.microsoft.com/api/search?search=*&locale=en-us)

> [!NOTE]
> We support the same locale codes that the docs site does.

### API Version [Optional]
To request a specific version, pass the api_version query string parameter. If no version parameter is passed, we will use the latest version. At present, the version is 0.1 (Beta). We will only change the API version, when the changes are incompatible with the existing version.[Example](https://docs.microsoft.com/api/search?search=*&locale=en-us&api_version= 0.1)

> [!IMPORTANT]
> We recommend passing the version.

### Filters
These sets of attributes will be used to further filter the search to certain content. Product can pass any metadata used by the content team. Clients can add multiple using logical ‘and’ and ‘or’.  [Example](https://docs.microsoft.com/api/search?search=*&locale=%20en-us&$filter=(scopes/any(t:t%20eq%20%27Unified%20Operations%27)%20and%20(validFrom%20lt%202017-03-31)))

[!INCLUDE [searchIndexes](searchIndexes.md)]

> [!NOTE]
> [Here](#interest-area-tags-aka-scope-aka-searchscope) is additional documentation on the 'scope' metadata.

> [!IMPORTANT]
> The values of filter are case sensitive.

> [!IMPORTANT]
> We highly recommend you to use one of the above metadata for filtering. If you still want to use other metadata, please inform your Docs onboarding PM with the names of metadata so that it can be added to the model.	

You can use the following operator to pass metatags
* eq: 
 * If the metadata tag is present and the value of the metatag is equal to the value of the attribute passed, then the content will be included in the search results. 
 * If the metadata tag is not present, then the content will NOT be included in the search results.
* ne: 
 * If the metadata tag is present and the value of the metatag is not equal to the value of the attribute passed, then the content will be included in the search results.
 * If the metadata tag is not present, then the content will be included in the search results.
* lt: 
 * If the metadata tag is present and the value of the metatag is less or equal to the value of the attribute passed, then the content will be included in the search results.
 * If the metadata tag is not present, then the content will be included in the search results.
* gt: 
 * If the metadata tag is present and the value of the metatag is greater or equal to the value of the attribute passed, then the content will be included in the search results.
 * If the metadata tag is not present, then the content will be included in the search results.

> [!IMPORTANT]
> Dates need to be in the [ISO-8601](https://en.wikipedia.org/wiki/ISO_8601 format).

## Search Results 

### Data and Format 
Following will be sent in the json format:
* results
* title
* url
* description – If description for the topic is not present, the first paragraph will be used as the description
* lastUpdatedDate
* breadcrumbs
* url
* name
* count
* @nextLink

### Results order
[!INCLUDE [search-resultsorder](search-resultsorder.md)]

### Pagination
1.	By default, the first 25 search results are passed.
2.	If the client needs specific number of results, ‘top’ attribute need to be passed to the service. If client passes more than 25, an error will be returned. [Example](https://docs.microsoft.com/api/search?search=General%20ledger&locale=en-us&$top=10)
3.	If the client needs next set of results, ‘skip’’ attribute need to be passed to the service. [Example](https://docs.microsoft.com/api/search?search=General%20ledger&locale=en-us&$top=10&$skip=10)

### Sample JSON file
```
{
    "results": [
        {
            "title": "Console",
            "url": "https://docs.microsoft.com/en-us/visualstudio/profiling/console",
            "description": "The VSPerfCmd.exe Console option starts the specified application in a new command prompt window. Console can only be used with the VSPerfCmd Launch option. If the application is not a command-line ap...",
            "lastUpdatedDate": "2016-11-04T00:00:00+00:00",
            "iconType": "Article",
            "breadcrumbs": [
                {
                    "url": "https://docs.microsoft.com/en-us/visualstudio/profiling/profiling-tools",
                    "name": "Profiling Tools"
                },
                {
                    "url": "https://docs.microsoft.com/en-us/visualstudio/profiling/performance-explorer",
                    "name": "Performance Explorer"
                },
            ]
        },
    ],
    "count": 5073,
    "@nextLink": "https://docs.microsoft.com/api/Search?locale=en-us&search=console&$skip=25&$top=25"
}
```

## Service Level Agreement
* Response Time: TBD
* Uptime: TBD
* Time-out: TBD

[!INCLUDE [search-scope](search-scope.md)]
