# I Want to Publish a Document with YAML Document Processor

OPS supports take an arbitrary YAML file as input and use it to generate an HTML file. This article will guide how to add a YAML file with a new document type, and how to add templates to process it.

## Introduction
In this tutorial, we'll add a new document type `NewGuide` with `.yml` as input. It can link to Markdown conceptual files.

[Here](https://github.com/superyyrrzz/TestNewGuide) is a sample repo containing the files in the tutorial for reference.

## Step1. Add Source Files

Firstly, let's create a content repo through OPS portal named `TestNewGuide`.

Now we can add a YAML file `TestNewGuide/guide.yml`:
``` yaml
### YamlMime:YamlDocument
documentType: NewGuide
title: Guide Title
items:
- title: Part One Title
  items:
  - title: Step 1
    href: part-1-step-1.md
- title: Part Two Title
  items:
  - title: Step 2
    href: part-2-step-1.md
```
Some explanation:
* `### YamlMime:YamlDocument`: This tells DocFX to use `YamlDocumentProcessor` to process this file. If not set, `.yml` files will be treated as a managed reference document by default.
* `documentType`: This tells DocFX which [template](http://dotnet.github.io/docfx/tutorial/intro_template.html) to apply.
* Other fields will be pass directly to raw model.

Change `TestNewGuide/docfx.json` to include `.yml` files:
```json
...
"files": [
  "**/*.md",
  "**/*.yml"
]
...
```
Then Add 2 Markdown files `TestNewGuide/part-1-step-1.md` and `TestNewGuide/part-2-step-1.md`:
``` md
# This is a step
This is some test content.
```
These are the normal conceptual markdown files. You can also add a YAML header with `documentType: NewStep` to specify another template.

## Step2. Add Templates

Let's create a [Mustache](http://mustache.github.io/) template `templates/NewGuide.html.primary.tmpl` for documentType `NewGuide`.
``` html
<div class="content">
  <h1>{{title}}</h1>
  {{#items}}
    <h2>{{title}}</h2>
    {{#items}}
      <a href="{{href}}">{{title}}</a>
    {{/items}}
  {{/items}}
</div>
```
And `templates/NewGuide.html.primary.js` to process the raw model:
``` js
exports.transform = function (model) {
  if (model.items) model.items.forEach(function (part) {
    if (part.items) part.items.forEach(function (step) {
      step.href = step.href.replace('.md', '.html');
    });
  });
  return model;
}
```
This preprocessor js:
* Updates the suffix of the href.
  > [!NOTE]
  > This is for demo purpose. It's not the recommended way to update href. As DocFX has the context of the mapping between input and output, DocFX will expose a funtion to update href later.

Then create a template `templates/NewGuide.mta.json.tmpl` for metadata file:
``` html
{{{content}}}
```
And `templates/NewGuide.mta.json.js` to process the raw model:
``` js
var opCommon = require('./op.common.js');

exports.transform = function (model) {
  model.layout = model.layout || "Conceptual";
  var resetKeys = [
    "items"
  ]
  model = opCommon.resetKeysAndSystemAttributes(model, resetKeys, true);
  return {
    content: JSON.stringify(model)
  }
}
```
Some explanation:
* The `layout` field tells DocFX to use `Conceptual.html.liquid` as the theme. You can also add another theme to themes repo (usually [templates.docs.msft](https://github.com/Microsoft/templates.docs.msft)) and specify it here.
* As metadata with complex value is not allowed to publish to DHS, we add `items` to `resetKeys` and remove them before publish.

Now the templates folder has 4 files: `NewGuide.html.primary.js`, `NewGuide.mta.json.tmpl`, `NewGuide.mta.json.js`, `NewGuide.mta.json.tmpl`. With these templates, the input `.yml` will have 2 outputs: `.html` and `.mta.json`. Then we should add folder `templates` to config file `.openpublishing.publish.config.json` so that DocFX can add these to template collection when builds:
``` json
 "docsets_to_publish": [
    {
      ...
      "customized_template_paths": [
        "templates"
      ]
      ...
    }
  ],
```
> [!NOTE]
> This step is unnecessary if the templates have been published to the themes repo [templates.docs.msft](https://github.com/Microsoft/templates.docs.msft). DocFX can pick up these templates automatically.

## Step3. Add Type Mapping
OPS knows which document type is content, so it can take extra steps to process content html. For the new type `NewGuide`, a type mappinig need to be added to `.openpublishing.publish.config.json`:
``` json
 "docsets_to_publish": [
    {
      ...
      "type_mapping": {
        "Conceptual": "Content",
        "ManagedReference": "Content",
        "RestApi": "Content",
        "NewGuide": "Content"
      },
      ...
    }
  ],
```
## Step4. Commit to trigger build
After these steps, the repo should has the following structure:
```
├── templates/
│   ├── NewGuide.html.primary.js
│   ├── NewGuide.html.primary.tmpl
│   ├── NewGuide.mta.json.js
│   └── NewGuide.mta.json.tmpl
│
├── TestNewGuide/
│   ├── guide.yml
│   ├── part-1-step-1.md
│   ├── part-2-step-1.md
│   └── docfx.json
│
└── .openpublishing.publish.config.json
```
Now the repo is ready to publish. Commit the change and push to remote, then OPS will build it and send a mail when it's complete.