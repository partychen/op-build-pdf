# Code Snippets

Inline code snippets, coloring, language selector, and external code snippets are now supported in OPS.

To see the content of this topic in markdown, click the **Edit** link in the right nav.

## Internal Code Snippets

You can reference code snippets stored in your repo by using the code language specified. The content of the specified code path will be expanded and included in your file.

We don’t have restrictions on the folder structure of code snippets. You should just manage the code snippets as normal source code.

Syntax:
```md
[!code[-<language>][<name>](<codepath><queryoption><queryoptionvalue> "<title>")]
```

* `-<language>` **OPTIONAL** Do not forget the '-' at the before the language name.
  * GFM currently supports only the following `<language>`values, retrievable by tag name (for more information, see [Highlight.js language names and aliases](http://highlightjs.readthedocs.org/en/latest/css-classes-reference.html#language-names-and-aliases)):
    * **C#**: cs, csharp
    * **C++**: cpp, c++
    * **F#**: fsharp
    * **HTML**: html
    * **JavaScript**: javascript
    * **PowerShell**: powershell, ps
    * **SQL**: sql
    * **Visual Basic**: vb, vbnet
    * **XML**: xml
  
  This value is used by frontend to do the code colorization. If it’s not specified, frontend will still do colorization for you based on the content of the code snippet but may not be accurate in some cases. 

* `<name>` **OPTIONAL** 
  * Name for the code snippet. It doesn’t have any impact on the output HTML but you can use them to improve the readability of your markdown source. It is added to be compatible with normal markdown link syntax, so it still renders as a link in markdown parser that doesn’t support OPS syntax (like GitHub). 

* `<codepath>` **MANDATORY** 
  * Relative path in the file system that indicates the code snippet file to reference.
* `<queryoption>` and `<queryoptionvalue>` **MANDATORY**
  * Used together to retrieve part of the code snippet file in the line range or tag name way. We have 2 query string options to represent these 2 ways:
    * `#`:  `#L{startlinenumber}-L{endlinenumber}`_ (line range) or _`#{tagname}`_ (tag name)
    * `?`:  `?start={startlinenumber}&end={endlinenumber}`_ (line range) or _`?{name}={tagname}`_ (tag name)
* `<title>` **OPTIONAL** 
  * Title for the code snippet. It doesn’t have any impact on the output HTML but you can use them to improve the readability of your markdown source. It is added to be compatible with normal markdown link syntax, so it still renders as a link in markdown parser that doesn’t support OPS syntax (like GitHub). 

### Code Snippet Sample
```md
[!code-csharp[Main](Program.cs)]

[!code[Main](Program.cs#L12-L16 "This is source file")]
[!code-vb[Main](../Application/Program.vb#testsnippet "This is source file")]

[!code[Main](index.xml?start=5&end=9)]
[!code-javascript[Main](../jquery.js?name=testsnippet)]
```

## External Code Snippets

You can reference code snippets stored in an external repository--a repo different from that in which your article resides--by using a method similar to #1 above, with two additional requirements.

* **Add external repo to repo config file**

  To reference an external repo, you must first add it to the `dependent_repositories` collection in your repo's **.openpublishing.publish.config.json** file found in the root of the repo. The format is as follows:

  ```json
  {
    "path_to_root": "name-of-repo",
    "url": "https://github.com/path/to/repo.git",
    "branch": "master"
  }
  ```

  For example, if you  want to include code found in [azure-storage-net](https://github.com/Azure/azure-storage-net) in an article in [azure-docs-pr](https://github.com/Microsoft/azure-docs-pr), add the following to the `dependent_repositories` section in [azure-docs-pr](https://github.com/Microsoft/azure-docs-pr)'s  [.openpublishing.publish.config.json](https://github.com/Microsoft/azure-docs-pr/blob/master/.openpublishing.publish.config.json):

  ```json
  {
    "path_to_root": "azure-storage-net",
    "url": "https://github.com/Azure/azure-storage-net.git",
    "branch": "master"
  }
  ```

  You can now reference **azure-storage-net** in your `<codepath>` (see next bullet).

* **Prefix relative \<codepath\> with for example `../../**`. Use relative path to include the code snippet based on the folder structure of both content repo and snippet repo.

  Now that you've added the dependent repository to the config file, you can reference code snippets using the following format:

  `[!code-language[name](../../repo-path-root/path/to/file.cs#TagName "Title")]`

  To follow on with the example above for **azure-storage-net**, a reference might look like:

   `[!code-csharp[tableinsert](../../azure-storage-net/Test/WindowsRuntime/Table/TableBatchOperationTest.cs#Insert "Table insert")]`

> [!IMPORTANT]
> Updating an external code snippet won’t auto trigger a content build. So you need to manually retrigger a build by either changing something in the doc repo or manually [kicking of a build](publish.md#ManualPublish). 

## Tabbed Code Snippets
> [!IMPORTANT]
> It only works for non-docs sites (MSDN, TN, and VisualStudio)

This works for both inline and external code snippets. You can have multiple samples grouped together so the user can see them in different tabs. 

> [!NOTE]
> If your code tabs aren't appearing as expected, check to ensure that the beginning and ending code tags (```) are flush left and not tabbed in.
<br />

Example:

````markdown
> [!div class="tabbedCodeSnippets"]
```cs
  var outlookClient = await CreateOutlookClientAsync("Calendar");
  var events = await outlookClient.Me.Events
    .Take(10)
    .ExecuteAsync();
  foreach(var calendarEvent in events.CurrentPage)
  {
    System.Diagnostics.Debug.WriteLine("Event '{0}'.", calendarEvent.Subject);
  }
```
```javascript
  outlookClient.me.events.getEvents().fetch().then(function (result) {
      result.currentPage.forEach(function (event) {
  console.log('Event "' + event.subject + '"')
      });
  }, function(error) {
      console.log(error);
  });
```
````

Will render as tabbed code snipppets in MSDN, TN, and VS.com. They will not render as tabbed codesnippets in OPS documentation or docs.microsoft.com as it is not supported by the template.

> [!div class="tabbedCodeSnippets"]
```cs
  var outlookClient = await CreateOutlookClientAsync("Calendar");
  var events = await outlookClient.Me.Events
    .Take(10)
    .ExecuteAsync();
  foreach(var calendarEvent in events.CurrentPage)
  {
    System.Diagnostics.Debug.WriteLine("Event '{0}'.", calendarEvent.Subject);
  }
```
```javascript
  outlookClient.me.events.getEvents().fetch().then(function (result) {
      result.currentPage.forEach(function (event) {
  console.log('Event "' + event.subject + '"')
      });
  }, function(error) {
      console.log(error);
  });
```

Note that the tab name could be specified as cs='C#', while it's optional for known languages, such as cs, cpp, javascript, for any unknown language, the tab name could only be shown if the mapping is specified in the div element. The feature depends on the frontend implementation to show the tab names correctly.
```markdown
> [!div class="tabbedCodeSnippets" cs='C#' javascript='Javascript']
```

## Interactive Code Snippets

> [!NOTE]
> This feature is only available on docs.microsoft.com.

Certain languages can be made interactive, allowing the code snipper to be executible from within the browser window.

We currently have the ability to enable Azure CLI code samples to be run directly from within docs.microsoft.com. Code samples for which this is enabled will now have a "Try It" button. Clicking that button will display the Azure Cloud Shell at the bottom of the screen. Here's an example:

```azurecli-interactive
az group create --name myResourceGroup --location westeurope
```

The integration we've built facilitates an authentication for customers so that *they can only run commands against their own Azure account.* This work has been done as part of a cross-org collaboration with the Azure Cloud Shell team.

To turn this feature on for a particular code block, you must use the language `azurecli-interactive` instead of `azurecli` for that code block. Here's the Markup for the above example:

    ```azurecli-interactive
    az group create --name myResourceGroup --location westeurope
    ```

The new Cloud Shell is also available for include blocks. Here's what that would look like:

```markdown
[!code-azurecli-interactive[main](../../../cli_scripts/virtual-machine/create-docker-host/create-docker-host.sh "Docker Host")
```