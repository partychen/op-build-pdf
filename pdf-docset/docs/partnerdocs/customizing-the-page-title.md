# Customizing The Page Title

When the docs platform displays your document, it ensures that the browser's `<title>` element is configured properly. This is the element which determines what is displayed in the browser's title bar or tab bar. The base value of the `<title>` element is determined as follows:

* If the document contains a `title` value in its metadata section, that value will be used for the title element.
* If the document does not contain a `title` value in its metadata section, the value of the first H1 in the document will be used for the document's title element.

Beyond this basic title, you can also set the `titleSuffix` global metadata in your `docfx.json` file to a string value. The intent of `titleSuffix` is to represent a product or service name that should be appended onto the title. e.g. `titleSuffix: Azure`. When added, every page in your docset will have the suffix value appended to the end of the page's title, using a dash (-) separator. Additionally, you can set this metadata value on an individual page. It's recommended that you use the global setting, but this capability allows you to override that on a per-page basis if required.

> [!NOTE]
> In addition to the above information being displayed in the document's title, every page on docs.microsoft.com will also have the text "Microsoft Docs" appended, with the pipe (|) as a separator. So, a full page title will often take the form `title - titleSuffix | Microsoft Docs`.
