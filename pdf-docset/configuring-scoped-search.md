# Configuring Scoped Search

docs.microsoft.com contains a mix of documentation from widely disparate products. A user who is viewing content within a single product area is unlikely to be interested in the entire set of documentation available on the site. For example, users viewing the .NET Core API reference are not necessarily the same people who want to view the Intune documentation. Given this, when a user decides to do a search from one of your pages, that search should be limited to the area of documentation that they are currently viewing. This is what Scoped Search enables you to do.

> [!IMPORTANT]
> Scoped search only works on the live environment and not in review.docs.microsoft.com

## How To Scope Searches

**Each docset should include a default set of search scopes.**

In order for content to participate in scoped search, you need to provide some additional configuration. Fortunately, you don't have to do this in every document. It can be done at the docset level, which is where you'll want to start.

> [!IMPORTANT]
> The review site doesn’t have its own search instance. So, the search results are based on what has been published. As a result, if you haven’t published anything with the scope, you won’t see it in the search results. Additionally, there’s a time delay between when a document is published and when it gets indexed by the search service. That can be anywhere between 0 and 30 hours.

### Strategy One: Docset Metadata

Our first step should be to update the search scopes for each docset. In the `docfx.json` file, add a new property to `globalMetadata` called `searchScope`. This property should contain an array of scope names.

Here's an example:

```json
"globalMetadata": {
  "ROBOTS": "NOINDEX, NOFOLLOW",
  "breadcrumb_path": "/openpublishing/test/breadcrumb.json",
  "_mockServerUrl": "https://apiexproxy.azurewebsites.net/svc",
  "_mockServerAuthorization": "Bearer {token:https://graph.windows.net/}",
  "is_e2e_test": true,
  "brand": "azure",
  "searchScope": ["Azure", ".NET"]
}
```

> [!NOTE]
> The value of `searchScope` is always an array, even if you only have one scope.
 
Declaring the `searchScope` metadata at the docset level ensures that all searches initiated from one of your docset pages will display only results that are also within the same scope. i.e. Documents inside your docset or that exist in another docset with the same scope configuration. The end user can see this indicated by the presence of a "chip" in the search box itself, which displays the scope name. You can see an example of this [in the .NET docs](https://docs.microsoft.com/en-us/dotnet/). As a result, it's important that you use a meaningful, human-readable scope name. If the user doesn't want to scope their searches to your area, the UX enables them to remove the scope and broaden their search.

> [!WARNING]
> The strings that are declared for `searchScope` are used by the seach engine *as is*. There is no mapping to alterantive representations, such as a *Display Name*. There is no master list of scopes either. As such, you need to ensure that a well-known set of human-readable scope names is used consistently across your content.

### Strategy Two: Document Metadata

In addition to `docfx.json` metadata, you can specify the same `searchScope` metadata at the document level. This overrides the global value for that document only.
 
Here's an example of what the metadata header might look like in an individual document:

```
ms.date: na
searchScope:
  - Azure
  - .NET
ms.prod: identity-ata
```

> [!NOTE]
> Remember, this will overwrite the docset-level metadata. It should only be used if the metadata at the docset level isn't appropriate or specific enough. This is not a general tagging mechanism. It is for broad search area scopes.