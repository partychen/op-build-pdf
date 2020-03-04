## Interest Area Tags aka scope aka searchScope
docs.microsoft.com contains a mix of documentation from widely disparate products. A user who is viewing content within a single product area is unlikely to be interested in the entire set of documentation available on the site. For example, users viewing the .NET Core API reference are not necessarily the same people who want to view the Intune documentation. Given this, when a user decides to do a search from one of your pages, that search should be limited to the area of documentation that they are currently viewing. This is what Scoped Search enables you to do.

The intention behind this tag is to identify the interest areas applicable to a certain article or group of articles. The tag is declared as `searchScope` at docset level and `scope` at article level. Scope can have multiple values because an article may belong to multiple interest areas. The first value is treated as the default scope. Scope is independent of other metadata and it doesn’t work in conjunction with other metadata. 

> [!WARNING]
> The strings that are declared for this tag are used by the site *as is*. There is no mapping to alterantive representations, such as a *Display Name*. There is no master list of scopes either. As such, you need to ensure that a well-known set of human-readable scope names is used consistently across your content.

> [!NOTE]
> * The value of `searchScope` is always an array, even if you only have one scope.
> * Same value of `searchScope` can be applied in multiple repositories and docset. All of these will be considered under this tag.

### Site features built on scope
There are two experiences built around scope. Here is additional documentation on how to define scope.
* If the content has defined scopes, we display the default scope (i.e the first scope for the content) in the search bar. When customer searches in the search bar, we will only display content in the search results that have that 'scope'. If the user doesn't want to scope their searches to your area, the UX enables them to remove the scope and broaden their search.
* [Upcoming] The user can filter the search results based on available scopes in the search result screen.
* [Upcoming] If the content has defined scopes, we will display all those scopes as RSS feed options. When customer uses one of these RSS feed, we will provide RSS feeds on all content have that 'scope'. 

### Defining Scope

#### Docset level
Our first step should be to update the search scopes for each docset. In the `docfx.json` file, add a new property to `globalMetadata` called `searchScope`.  Declaring the `searchScope` metadata at the docset level ensures that all searches initiated from one of your docset pages will display only results that are also within the same scope. i.e. Documents inside your docset or that exist in another docset with the same scope configuration. 
Here's an example:

```json
"globalMetadata": {
  "breadcrumb_path": "/openpublishing/test/breadcrumb.json",
  "_mockServerUrl": "https://apiexproxy.azurewebsites.net/svc",
  "_mockServerAuthorization": "Bearer {token:https://graph.windows.net/}",
  "is_e2e_test": true,
  "brand": "azure",
  "searchScope": ["Azure", ".NET"]
}
```

#### Folder level
You can **override** the docset search scope by specifying scope at folder level. Here's an example:

```json
"fileMetadata": { 
    "searchScope": { "articles/uwp/**.md": ["Windows","UWP"] } 
}
```

#### Article level
In addition to `docfx.json` metadata, you can specify the same `searchScope` metadata at the document level. This **overrides** the global value for that document only. Here's an example of what the metadata header might look like in an individual document:

```
ms.date: na
searchScope:
  - Azure
  - .NET
ms.prod: identity-ata
```

> [!NOTE]
> Remember, this will overwrite the docset-level metadata. It should only be used if the metadata at the docset level isn't appropriate or specific enough. This is not a general tagging mechanism. It is for broad search area scopes.

### Examples

#### Example 1
Following is the configuration
* Repository - Windows
 * Docfx file
  * "globalMetadata": { "searchScope": ["Windows"], }
  * "fileMetadata": { "searchScope": { "articles/uwp/**.md": ["Windows","UWP"] } }
 * Articles/uwp/article1.md
  * <meta name="scope" content=["Windows","UWP",”Windows Fluent Design”] /
 * Articles/uwp/article2.md
  * No scope defined.
 * Articles/iot/article3.md
  * No scope defined.

This will be the behavior
* If I search within “Windows” scope, I will see article 1, article 2 and article 3
* If I search within “UWP” scope, I will see article 1 and article 2 
* If I search within “Windows Fluent Design” scope, I will see article 1
* When I go to article 1, article 2 and article 3, “Windows” will be the default scope in the search bar.

#### Example 2
Following is the configuration
* Repository : UWP Apps
 * Docfx.json
  * "globalMetadata": { "searchScope": ["Windows”, “UWP”], }	
* Repository : Desktop
 * Docfx.json
  * "globalMetadata": { "searchScope": ["Windows”, “Desktop”], }	
* Repository : Microsoft Edge
 * Docfx.json
  * "globalMetadata": { "searchScope": ["Windows”, “Edge”], }	

This will be the behavior
* Your default scope will be “Windows” so customer will see Windows on the search bar
* When customer searches on Windows scope, they will see results from all the three repositories.




