# TOC Creation and Management #

A **ToC** is used to define the Table of Contents (ToC) structure of a docset. The ToC can be described using either Yaml or Markdown.

## Yaml ToCs

The recommended format for ToCs is Yaml. The Yaml-based ToC format enables additional capabilities, such as auto-expansion of ToC nodes and automatic contextual ToC query string generation, which aren't available when using Markdown.

To build your ToC with Yaml, you should create a file named `toc.yml`. Let's look at how a simple ToC would be represented:

```yaml
- name: Tutorial
  href: tutorial.md
  items:
  - name: Step 1
    href: step-1.md
  - name: Step 2
    href: step-2.md
  - name: Step 3
    href: step-3.md
```

The Yaml document itself is a list of ToC elements, each of which minimally has a `name` and `href`. ToC nodes can also act as parents to other nodes. In this case, the child ToC nodes are represented by a list called `items`.

What follows is a larger example Yaml structure, which demonstrates more configuration options:

```yaml
- name: Dev Sandbox
  href: index.md
  displayName: Home
  pdf_name: foo
- name: Conceptual Pages
  href: ./conceptual/index.md
  expanded: true
  items:
  - name: Code Samples
    href: ./conceptual/code.md
  - name: Tables
    href: ./conceptual/tables.md
- name: Reference Pages
  items:
  - name: IDictionary
    href: ./reference/System.Collection.IDictionary.yml
  - name: String
    href: ./reference/System.String.yml
- name: Content Pages
  href: ./content/index.md
- name: Hub Pages
  items:
  - name: Card Gallery
    href: ./hubPage/cardGallery.md
- name: Landing Pages
  items:
  - name: Azure Architecture
    href: ./landingPage/azureCat.md
  - name: UWP
    href: ./landingPage/uwp.md
- name: Engineering Excellence
  items:
  - name: Environment Setup
    href: ./eeds/environment-setup.md
  - name: Template Docs
    href: ./eeds/docs/index.md
- name: Break Title Tests
  items:
  - name: System.Automation.String.Foo.Bar.Zip.Test()
    href: ./eeds/environment-setup.md
  - name: VMScaleSets-AzureRmDiagnosticsDscFixUp
    href: ./eeds/docs/index.md
```

Here's an explanation of all the properties available on a ToC node:

* `name` (required) - A string name that is displayed for the ToC node.
* `displayName` (optional) - An additional string value that doesn’t get displayed (yes, it's a very poor name) but is searched, in addition to `name`, when doing ToC filtering.
* `href` (optional) - A string that represents the link that the ToC node navigates to. Remember, nodes can exist just to parent other nodes, so this is still an optional property.
* `items` (optional) - If a node has children, those are listed in the `items` array. The child nodes have the same available properties as listed above.
* `expanded` (optional) - A boolean property (true/false) that determines if the node should be expanded by default when the ToC is loaded. Only *one* root-level node can be expanded on load.
* `maintainContext` (optional) -  A boolean property (true/false) that determiens if the ToC should be passed along with the link, for contextual ToC purposes. When using this property to reference an article in another docset, you don't have to encode the contextual ToC in the query string.

> [!NOTE]
> The Yaml format is more verbose that the Markdown format you will see next, but it enables taking advantage of the additional properties such as `displayName`, `expanded` and `maintainContext`. Future capabilities coming to ToCs, such as versioning and experimentation, will similarly require Yaml.

Ultimately, we'd like to move ToCs to the Yaml-based format, so all new ToCs should be created this way going forward. If you have an existing ToC that you need to migrate, please reach out to Rob Eisenberg or Duncan Mackenzie to learn about available migration tools.

> [!IMPORTANT]
> In your docfx.json file, in your `content.files` section, make sure to add the glob `"**/*.yml"`, otherwise the build system will not pick up the Yaml file.

## Markdown ToCs

To build your ToC with Markdown, you should create a file named `toc.md`. Let's look at how a simple ToC would be structured:

 ```markdown
# Tutorial
## Step 1
## Step 2
## Step 3
```

The above example illustrates a parent topic "Tutorial" with three children Step 1-3.

We use standard Markdown link syntax to specify the target topic of the toc node. For example:

```markdown
 # [Tutorial](tutorial.md)
 ## [Step 1](step-1.md)
 ## [Step 2](step-2.md)
 ## [Step 3](step-3.md)
```

If a toc node is not a link, it will become a container node: it can contain children and it will be just a expanding/collapsing node.

## Nested ToCs

Some times you would like to split your giant ToC file to multiple smaller managable pieces. OPS also supports this approach. During build, we will find the ToC files referenced by the main ToC and generate a combined ToC view.

You can find 2 different syntax below, as we support either referencing another ToC file, or a folder. 

 - If you include a toc.md file, the entry you use to include the file would be rendered as a control to expand or collapse the sub ToC.
 - If you include a folder, OPS will NOT extract the toc.md in that folder, but use the 1st entry in the toc.md file in that folder as the entry in the referencing TOC.  

```markdown
# [Root Index](index.md)
## [1-1 topic](1-1topic.md)
## [1-2 topic](1-2topic.md)
## [ref 2-1 toc](level-2-1/TOC.md)
## [ref 2-2 folder](level-2-2/)
```

The level of ToC entry would be the calculated a sum from the referencer and referencee ToC file for the specific entry.

TOC common issues:

1)	Remove the root folder, some paths had the root folder in it and it is not needed.
a.	Good: marketplace/overview.md
b.	Not good: /docs/marketplace/overview.md
2)	Others had an extra slash
a.	Good: collaborate/overview.md
b.	Not good: /collaborate/overview.md
3)	Others had the wrong abbreviation for the path:
a.	Good: ./docs/setup-admin/get-started.md
b.	Not good: ../ docs/setup-admin/get-started.md


> [!NOTE]
> OP supports multiple level of nested ToC - 6 levels maximum.
> OP doesn't support nested TOCs between docsets or repos. 

## Important Information

- The ToC for Open Publishing is a self-contained ToC, not integrated into the global MSDN/TN ToC.
- You can use an external link to connect the Open Publishing ToC to your MSDN/TN Global ToC.
- Since Markdown only supports 6 levels of header, we'll only support 6 levels of ToC for now. This can be extended in the future.
- You cannot reference a file outside a docset/folder. 
- toc.md cannot contain arbitrary Markdown content. For example, you cannot have images in it. All content that are not headers will lead to a build error.

## Localized ToCs

A localized ToC is maintained in sync with English via the handoff and handback process. The ToC file will be included in the handoff package. 

## Suggested ToC Structure

To ensure quality, standarization and a great user experience we recommend that the ToC follows this structure:

```markdown
# [Overview](overview.md)
## [topic-related-to-Overview](topic-related-to-Overview.md)
# [Getting Started](Getting-Started.md)
## [topic-related-to-gettingstarted](topic-related-to-gettingstarted.md)
# [How to](How-to.md)
## [topic-related-to-hot-to](topic-related-to-hot-to.md)
# [Reference](reference.md)
## [topic-related-to-reference](topic-related-to-reference.md)
# [Resources](resources.md)
## [topic-related-to-resources](topic-related-to-resources.md)
 ```

Topic across Azure follow this ToC guideline for consistency and quality, example: [Azure Express Route](https://docs.microsoft.com/en-us/azure/expressroute/). 

Azure Standarized TOC:
![](./media/ideal-toc.png)

## Convert yout MD TOC to a YAML TOC
There is a tool that can convert MD to Yaml TOCs. Verndors might know about this tool.

## Further Information

As OPS uses [DocFX](http://dotnet.github.io/docfx/) for transforming the content, as well as the ToC, you can find additional information in [this set of instructions](http://dotnet.github.io/docfx/tutorial/intro_toc.html). 
