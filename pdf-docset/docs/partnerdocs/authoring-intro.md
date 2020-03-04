# Authoring Introduction

Authoring documentation for OPS involves gaining a basic competency in three specific technologies:

* Git
* Markdown
* Yaml

**Git** is a distributed version control system that forms the basis of how OPS handles documentation provisioning, build and publication. All documentation content exists in a Git repo somewhere, either on GitHub (for public documentation) or in VSO (for private documentation). As you work to create content for your documentation, you'll create Git commits and push them to various branches. Working with contributors is as simple as accepting pull requests (PRs) from anyone who has access to your Git repository.

**Markdown** is a lightweight markup language with plain text formatting syntax. It is designed so that it can be converted to HTML and many other formats using a tool by the same name. Markdown forms the basis of our documentation's conceptual authoring language. Creating new articles is as easy as writing a simple text file using your favorite text editor.

**Yaml** is a human-readable data serialization language. It is commonly used for configuration files. YAML targets many of the same scenarios as XML, but has taken a more minimal approach allowing users to leverage white space instead of braces, brackets or other symbols. OPS uses Yaml for portions of the documentation experience that rely on structured data. Examples of this include your Table of Contents (ToC), Landing Pages, API Reference, and more.