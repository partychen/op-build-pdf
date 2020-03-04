# Yaml

**Yaml** is a human-readable data serialization language. It is commonly used for configuration files. YAML targets many of the same scenarios as XML, but has taken a more minimal approach, allowing users to leverage white space instead of braces, brackets or other symbols. OPS uses Yaml for portions of the documentation experience that rely on structured data. Examples of this include your Table of Contents (ToC), Landing Pages, API Reference, and more.

## Yaml Basics

Here's a great video introduction to Yaml.

[!Video https://www.youtube.com/embed/W3tQPk8DNbk]

You can also visit [the author's learning site for a written explanation of Yaml](https://learn-the-web.algonquindesign.ca/topics/yaml). He's also put together [a handy cheat sheet](https://learn-the-web.algonquindesign.ca/topics/markdown-yaml-cheat-sheet/) that has both Yaml and Markdown syntax in the same page. Here's [another quick cheat sheet](https://learnxinyminutes.com/docs/yaml/) showing a variety of Yaml capabilities.

## Yaml Tooling

All you need to write Yaml is a basic text editor. Just remember that Yaml is whitespace sensitive and that you'll need to use two spaces for indentation, always.

Here are a few links to tools that may help you:

* http://www.yamllint.com/ - Take any Yaml you've written, paste it into the text box and press a button to validate it.
* https://marketplace.visualstudio.com/items?itemName=djabraham.vscode-yaml-validation - A VS Code plugin for validating Yaml syntax.
* https://marketplace.visualstudio.com/items?itemName=aaubry.YAMLEditor - A Yaml Editor plugin for Visual Studio.

## Yaml Within Docs

Yaml is used to handle a variety of scenarios in OPS. Below are a few places that Yaml is being used or where we plan to use it in the future:

* **ToC** (available) - ToCs are basically a hierarchy of named links. This is a perfect fit for Yaml, which is good at modeling object hierarchies and lists.
* **Hub/Landing Pages** (partial) - In many ways, Hub and Landing pages are like fancy ToCs. They are comprised of pivots, tabs, bands, sections and links. Sometimes links have images and descriptions that accompany them. The various bands can be laid out in different arrangements: one-column, two-column, etc. Yaml is perfect for representing this type of structured data.
* **Tutorials** (in progress) - Tutorials are yet another scenario that is similar to a ToC. Tutorials require special information, such as Audience and Level. They also have an ordered lists of steps, each of which has a name, link and duration. Yaml fits this type structured data model nicely.
* **Universal Reference** (in progress) - Reference documentation is extracted from actual code. It represents ideas like modules, packages, namespaces, classes, functions, methods, etc. Programming languages structure their programs with these primitives. The OPS platform models these ideas as part of its Universal Reference language and the data itself is encoded into Yaml for easy and consistent projection into HTML.
* **Context** (in progress) - Every time a piece of content is rendered by docs, it's rendered within a specific "context". The context defines what header, breadcrumbs and ToC are rendered around the core content. These contexts can be configured through Yaml and can be attached to content in OPS.

Each usage of Yaml involves writing Yaml that is not only syntactically correct, but that also adheres to the proper schema. Work is currently underway to define schemas for the above scenarios and integrate them into tooling so that content authors can validate the correctness of their configurations.