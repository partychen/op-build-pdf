# Creating a Contextual ToC

Often times you may want to compose a ToC from documents which live in other repositories or that already have an associated default ToC. By default, when a reader clicks on a ToC link and navigates to one of these pages, they'll see the ToC change to the default ToC associated with the target page, replacing the ToC that they just clicked on. This causes a jarring experience and rips the reader out of their correct documentation context, landing them in a potentially foreign location. By using the "Contextual ToC" feature, you can configure any ToC link so that it carries with it a ToC that is different from its default ToC.

## How To Use Contextual ToC

To use contextual ToC, simply append a `toc` query string parameter onto any conceptual link url, ensuring that the parameter's value is equal to a ToC url relative to docs.microsoft.com (minus the locale segment).

For example, let's say there's a nice article in Enterprise Mobility, `some-article`, that we want to include inside the .NET ToC. When a customer clicks on the link from within .NET, we want them to not only see the Enterprise Mobility content, but we also want them to remain inside the .NET ToC. To override the default ToC associated with the Enterprise Mobility article, we would create the link with the following url:

```md
https://docs.microsoft.com/en-us/enterprise-mobility/some-article?toc=/dotnet/toc.json
```

In this case we have the article link, `https://docs.microsoft.com/en-us/enterprise-mobility/some-article` which is instructing docs to display a different ToC with `?toc=/dotnet/toc.json` based on the ToC located at `https://docs.microsoft.com/en-us/dotnet/toc.json`

For a situation where the breadcrumb also needs to change (which is in most cases), an additional parameter of `bc` needs to be specified, in this manner:

```md
https://docs.microsoft.com/en-us/enterprise-mobility/some-article?toc=/dotnet/toc.json&bc=/dotnet/breadcrumb/toc.json
```

> [!NOTE]
> Linking from within Enterprise Mobility, to pages that share the same ToC, does not require the `toc` or `bc` query strings because the default ToC will be picked up.