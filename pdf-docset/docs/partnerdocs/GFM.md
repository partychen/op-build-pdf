## Getting Started with Markdown

**Markdown** is a lightweight markup language with plain text formatting syntax. It is designed so that it can be converted to HTML and many other formats using a tool by the same name. Markdown forms the basis of our documentation's conceptual authoring language. Creating new articles is as easy as writing a simple text file using your favorite text editor.

## Markdown Supported by OPS
DocFX, used by OPS, supports "DocFX Flavored Markdown," (DFM). It is highly compatible with GitHub Flavored Markdown (GFM), and adds some additional functionality, including cross reference and file inclusion. There are [Differences between DFM and GFM] (http://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#differences-between-dfm-and-gfm) that can affect content preview in GitHub, VSTS, or your editor.

## Markdown Tutorials

Here are two great tutorials for Markdown and GitHub Flavored Markdown:

- [Introduction to Markdown by John Gruber](http://daringfireball.net/projects/markdown/syntax)
- [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/)

## Choosing an Editor
You can use any Markdown editor you would like to edit Markdown. Some suggestions: [MarkdownPad](http://markdownpad.com/), [Visual Studio Code](https://www.visualstudio.com/en-us/products/code-vs.aspx), [Markdown Mode](https://visualstudiogallery.msdn.microsoft.com/0855e23e-4c4c-4c82-8b39-24ab5c5a7f79). 

Most of them provide live preview functionality so that you can get a simple preview when writing the topic. The preview will differ from the final rendering for extensions and places where DFM differs from GFM.

## Markdown Extensions Supported by Open Publishing
The following contains the list of supported extensions in Open Publishing. 

### File Includes
You can include other file into the current file; the included file will also be configured in DFM syntax. 

> [!NOTE]
> YAML header is **NOT** supported when the file is an inclusion.

There are three types of file inclusion: inline, block, and image.

#### Inline Includes
Inline file inclusion is in the following syntax, in which `<title>` stands for the title of the included file, and `<filepath>` stands for the file path of the included file; the file path must be a relative file path. Absolute path is not supported. `<filepath>` can be wrapped by `'` or `"`. Note that for inline file inclusion, the file included will be considered as containing only inline tags, e.g. `###header` inside the file will not be transformed because `<h3>` is a block tag, while `[a](b)` will be transformed to `<a href='b'>a</a>` because `<a>` is an inline tag.

```
...Other inline content... [!include[<title>](<filepath>)]
```

#### Block Includes
Block file inclusion must be in a single line and with no prefix characters before the start `[`. Content inside the included file will be transformed using DFM syntax.

```md
[!include[<title>](<filepath>)]
```
#### Images
The syntax to include an image is `![[alt text]]({folderPath})` 

Example: `![alt-text for image](../images/Introduction.png)`

Provide a descriptive  alternate text for an image. We even support animated gifs! 
 
Example: Following the same syntax: `![Responsive design](../images/responsivedesign.gif)`

![Responsive design](../images/responsivedesign.gif)

### Note, Warning, Tip, Important, Caution
Use specific syntax inside a block quote to indicate that the content following is a Note.

```
> [!NOTE]
> This is a NOTE

> [!WARNING]
> This is a WARNING

> [!TIP]
> This is a TIP

> [!IMPORTANT]
> This is IMPORTANT

```

And it will render like:

> [!NOTE]
> This is a NOTE

> [!WARNING]
> This is a WARNING

> [!TIP]
> This is a TIP

> [!IMPORTANT]
> This is IMPORTANT

### Checked Lists

> [!NOTE]
> This feature is only available on docs.microsoft.com.

A custom style is  available for bulleted lists. You can render lists with check marks. Here's an example:

> [!div class="checklist"]
> * Log in to Azure
> * Create a resource group
> * Prepare the configuration
> * Create a virtual machine
> * Configure the firewall
> * Snapshot the virtual machine
> * Run management tasks

To render the above list, you would write the following Markdown:

```markdown
> [!div class="checklist"]
> * Log in to Azure
> * Create a resource group
> * Prepare the configuration
> * Create a virtual machine
> * Configure the firewall
> * Snapshot the virtual machine
> * Run management tasks
```

While this new Markdown extension can be used anywhere, we recommend that you target this towards the "What will you learn" (at the top of an article) or "What have you learned" (at the end of an article) scenarios, where you want to vividly point out to customers key points they will learn in an article or tutorial. Please refrain from adding random or ad hoc checked lists throughout your articles.

### Next Step Action

> [!NOTE]
> This feature is only available on docs.microsoft.com.

This extension is targeted at providing a consistent way for writers to show a next step action at the end of their articles. Here's an example:

> [!div class="nextstepaction"]
> [Create and Manage VM disks](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-manage-disks)

To render the above action, you would write the following Markdown:

```markdown
> [!div class="nextstepaction"]
> [Create and Manage VM disks](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-manage-disks)
```

Please use this Markdown extension only at the end of your articles, with the explicit intent to guide readers to a next article that they should read after their currently viewed article. Please do not use this extension in any other way.

### Links
Adding links to other content in OPS is a very common use case and OPS has a capability to resolve and validate the links in below situations.

#### Reference Content Within a Docset
In OPS, the build system treat docsets as the boundary for reference validation. So for any link reference within a docsets, the build service is able to resolve and validate that link in common GFM Markdown syntax. Thus, content owners can use a relative path as shown below to create a link reference within the same docset. 

```md
[My link text](../active-directory/active-directory-article-name.md)
```

#### Reference Content in External Docsets
OPS currently doesn't support resolving and validating logic for cross-docset reference. So if you want to reference a file in another docsets, you need to add a cross-docset reference by using *absolute path reference*. For example:

```md
[My link text](/active-directory/active-directory-article-name)
```
the "/active-directory/active-directory-article-name" is part of the full URL without the domain, so it creates a link to https://{Domsin}/active-directory/active-directory-article-name

#### Anchor Links

Anchor links allow you to go to a section of a specific topic. 

Markdown headings H2 (##) through H6 (######) are automatically anchors. The anchor ID is the full text of the heading, all lowercase, with punctuation removed and dashes instead of spaces. For example, the ID for the heading `## 2. Getting started with Markdown` is `2-getting-started-with-markdown`.

To link to this heading in the current file, use:

`[getting started](#2-getting-started-with-markdown)`

It renders like this:

[getting started](#2-getting-started-with-markdown)

To link to a heading from another topic, use the relative link to the current topic, plus `#` followed by the anchor ID, such as:

`[getting started with GFM](../gfm.md##2-getting-started-with-markdown)`

Explicit anchors using `<a>` are not required except in hub and landing pages:

`## <a id="AnchorText"> </a>Header text`
or
`## <a name="AnchorText"> </a>Header text`

And the following for the link to it:

* `Go to [text](#AnchorText)` to go to the topic within the same page.
    * Example: Go to [top of the page](#Top).
* `Go to [text](FileName.md#AnchorText)` to go to the topic to another page.
    * Example: See [publish configuration](publish-configuration.md#publish-config-need_generate_intellisense) for more information.

### xRef Links

To link to an API topic by `uid`, use an `xref` link:

`<xref:uid>`

Such as: `<xref:System.String>` or `<xref:microsoft.azure.keyvault.keyidentifier.iskeyidentifier>`

To link to an overload overview page, add `2%a`:

`<xref:System.String.Format2%A>`

To link to a specific overload, inlcude the parameters in the `uid`:

`<xref:System.String.Format(System.String,System.Object)>`

To render the full API name in the link, such as System.String instead of String, add  `?displayProperty=fullname`:

`<xref:System.String?displayProperty=fullName>`

Target API docs must be in the same repo or in a cross reference map in the repo. For more information, see [DocFx: Links and Cross References](http://dotnet.github.io/docfx/tutorial/links_and_cross_references.html).

### Section Definition
A user may need to define a section. This is mostly used for code tables.
See the following example.

````
> [!div class="tabbedCodeSnippets" data-resources="OutlookServices.Calendar"]
> ```cs
> <cs code text>
> ```
> ```javascript
> <js code text>
> ```
````

The preceding blockquote markdown text will render as:
> [!div class="tabbedCodeSnippets" data-resources="OutlookServices.Calendar"]
> ```cs
> <cs code text>
> ```
> ```javascript
> <js code text>
> ```

### Code Snippets
See [Code snippets page](codesnippets.md).

### Metadata

See [Metadata](metadata.md).

### Selector

Selector can be used when partner would like to connect different pages for the same topic and allow user to switch between those topics. 
> [!NOTE]
> This extension works different between docs.microsoft.com and MSDN 

#### Single Selector
```
> [!div class="op_single_selector"]
> - [Universal Windows](../articles/notification-hubs-windows-store-dotnet-get-started/)
> - [Windows Phone](../articles/notification-hubs-windows-phone-get-started/)
> - [iOS](../articles/notification-hubs-ios-get-started/)
> - [Android](../articles/notification-hubs-android-get-started/)
> - [Kindle](../articles/notification-hubs-kindle-get-started/)
> - [Baidu](../articles/notification-hubs-baidu-get-started/)
> - [Xamarin.iOS](../articles/partner-xamarin-notification-hubs-ios-get-started/)
> - [Xamarin.Android](../articles/partner-xamarin-notification-hubs-android-get-started/)
```
And it will render like
> [!div class="op_single_selector"]
> - [Universal Windows](../index.md)
> - [Windows Phone](../index.md)
> - [iOS](../index.md)
> - [Android](../index.md)
> - [Kindle](../index.md)
> - [Baidu](../index.md)
> - [Xamarin.iOS](../index.md)
> - [Xamarin.Android](../index.md)

### Multi Selector
```
> [!div class="op_multi_selector" title1="Platform" title2="Backend"]
> - [(iOS | .NET)](./mobile-services-dotnet-backend-ios-get-started-push.md)
> - [(iOS | JavaScript)](./mobile-services-javascript-backend-ios-get-started-push.md)
> - [(Windows universal C# | .NET)](./mobile-services-dotnet-backend-windows-universal-dotnet-get-started-push.md)
> - [(Windows universal C# | Javascript)](./mobile-services-javascript-backend-windows-universal-dotnet-get-started-push.md)
> - [(Windows Phone | .NET)](./mobile-services-dotnet-backend-windows-phone-get-started-push.md)
> - [(Windows Phone | Javascript)](./mobile-services-javascript-backend-windows-phone-get-started-push.md)
> - [(Android | .NET)](./mobile-services-dotnet-backend-android-get-started-push.md)
> - [(Android | Javascript)](./mobile-services-javascript-backend-android-get-started-push.md)
> - [(Xamarin iOS | Javascript)](./partner-xamarin-mobile-services-ios-get-started-push.md)
> - [(Xamarin Android | Javascript)](./partner-xamarin-mobile-services-android-get-started-push.md)
```
And it will render like 
> [!div class="op_multi_selector" title1="Platform" title2="Backend"]
> - [(iOS | .NET)](../index.md)
> - [(iOS | JavaScript)](../index.md)
> - [(Windows universal C# | .NET)](../index.md)
> - [(Windows universal C# | Javascript)](../index.md)
> - [(Windows Phone | .NET)](../index.md)
> - [(Windows Phone | Javascript)](../index.md)
> - [(Android | .NET)](../index.md)
> - [(Android | Javascript)](../index.md)
> - [(Xamarin iOS | Javascript)](../index.md)
> - [(Xamarin Android | Javascript)](../index.md)

### Video Syntax
Currently, OPS can support video syntax for Channel 9 (CH9) and youtube videos. User can embed the video with the following syntax and OPS will render it.

```markdown
> [!VIDEO <channel9_video_link>]
> [!VIDEO <youtube_video_link>]
```

Sample:
```markdown
> [!VIDEO https://channel9.msdn.com/Series/Youve-Got-Key-Values-A-Redis-Jump-Start/03/player]
> [!Video https://www.youtube.com/embed/XGSy3_Czz8k]
```


It will render as:
```html
<iframe src="https://channel9.msdn.com/Series/Youve-Got-Key-Values-A-Redis-Jump-Start/03/player" width="640" height="320" allowFullScreen="true" frameBorder="0"></iframe>
<iframe src="https://www.youtube.com/embed/XGSy3_Czz8k" width="640" height="320" allowFullScreen="true" frameBorder="0"></iframe>
```

And display like this on published pages:

> [!VIDEO https://channel9.msdn.com/Series/Youve-Got-Key-Values-A-Redis-Jump-Start/03/player]

> [!Video https://www.youtube.com/embed/XGSy3_Czz8k]

> [!NOTE]
> The CH9 video url should start with `https` and end with `/player`. Otherwise, it will embed the whole page instead of the video only.

## Resolve File Path

 1. Relative path (path like foo/bar.md) is the path relative to the file where this path is written, which means in file include case, it’s relative to the included file. For example, we have A.md includes B.md, B.md has a relative path in it. Then that path is relative to B.md instead A.md.
 2. Relative path will be resolved during build (remove .md extension), and generate build warning if target file doesn’t exist.
 3. You can use “../” to link to file in parent folder, but that file has to be in the same docset. You cannot use “../” to link to a file in another docset folder.
 4. We also support a special form of relative path which starts with ~ (for example, ~/foo/bar.md), which means a file relative to the root folder of a docset. This kind of path will also be validated and resolved during build.
 5. Besides markdown link and image, you can also use relative path in html link (<a>) and image (<img>).
 6. Absolute path (path starts with /) means a path in the output website. We don’t process absolute path and leave it as-is in output html. This means if you use absolute path, you need to add the base url and remove the .md extension by yourself.

## HTML Whitelist

You can embed HTML code into your content, as long as it is within the GitHub Whitelist. **We also enable iframe element for video embedding even though it is not in the GFM whitelist**. HTML rendered by the various markup language processors gets passed through an [HTML sanitization filter](https://github.com/jch/html-pipeline/blob/master/lib/html/pipeline/sanitization_filter.rb) for security reasons. HTML elements not in the whitelist are removed. HTML attributes not in the whitelist are removed from the preserved elements.

The following HTML elements, organized by category, are whitelisted:

Type | Elements  
---------|---------
Headings     |  h1, h2, h3, h4, h5, h6    
Prose     |  p, div, blockquote       
Formatted     |   pre      
Inline     |     b, i, strong, em, tt, code, ins, del, sup, sub, kbd, samp, q, var    
Lists     |   ol, ul, li, dl, dt, dd      
Tables     | table, thead, tbody, tfoot, tr, td, th        
Breaks     |   br, hr      
Ruby (East Asian)     |   ruby, rt, rp      
Video (not in GFM whitelist)    |  iframe
Comments | Comments

The following attributes, organized by element, are whitelisted:

Element  |Attributes  
---------|---------
a     |      href (http://, https://, mailto://, github-windows://, and github-mac:// URI schemes and relative paths only)   
iframe |  src, allowFullScreen, frameBorder, scrolling
img     |     src (http:// and https:// URI schemes and relative paths only)    
div     |     itemscope, itemtype    
All     |     abbr, accept, accept-charset, accesskey, action, align, alt, axis, border, cellpadding, cellspacing, char, charoff, charset, checked, cite, clear, cols, colspan, color, compact, coords, datetime, dir, disabled, enctype, for, frame, headers, height, hreflang, hspace, ismap, label, lang, longdesc, maxlength, media, method, multiple, name, nohref, noshade, nowrap, prompt, readonly, rel, rev, rows, rowspan, rules, scope, selected, shape, size, span, start, summary, tabindex, target, title, type, usemap, valign, value, vspace, width, itemprop    

Note that the id attribute is not whitelisted.

## Tables
The simplest way to create a table in markdown is to use pipes and lines.

 ![](./media/table-markdown.png)

You can justify the columns with colons:

    |-----:| - this is right aligned
    |:-----| -  this is left aligned
    |:-----:| - this is centered

You can create a table without a header. For example, to create a multi-column list:

```
|   |   |
| - | - |
| This | table |
| has no | header |
```

If you use HTML tables and your markdown is not rendering between the two tables, you need to add a closing BR tag after the closing TABLE tag.

 ![](media/break-tables.png)

For more information about how to create tables in markdown, see:

* Markdown tables generator: http://www.tablesgenerator.com/markdown_tables
* https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#wiki-tables
* http://michelf.ca/projects/php-markdown/extra/#table

## Table Wrapping

> [!IMPORTANT]
> This feature only works on docs.microsoft.com site.

If you create a table in Markdown, often times the table might expand to the right nav, making the table unreadable. You can solve that easily by allowing docs rendering to break the table when needed. You just need to wrap up the table with the ccustom class ` [!div class="mx-tdBreakAll"]`

Here is a Markdown sample of a table with three rows that will be wrapped by a div with the class name “mx-tdBreakAll”.

```
> [!div class="mx-tdBreakAll"]
> |Name|Syntax|Mandatory for silent installation?|Description|
> |-------------|----------|---------|---------|
> |Quiet|/quiet|Yes|Runs the installer displaying no UI and no prompts.|
> |NoRestart|/norestart|No|Suppresses any attempts to restart. By default, UI will prompt before restart.|
> |Help|/help|No|Provides help and quick reference. Displays the correct use of the setup command including a list of all options and behaviors.|
```

It will render like this:

> [!div class="mx-tdBreakAll"]

> |Name|Syntax|Mandatory for silent installation?|Description|
> |-------------|----------|---------|---------|
> |Quiet|/quiet|Yes|Runs the installer displaying no UI and no prompts.|
> |NoRestart|/norestart|No|Suppresses any attempts to restart. By default, UI will prompt before restart.|
> |Help|/help|No|Provides help and quick reference. Displays the correct use of the setup command including a list of all options and behaviors.|

