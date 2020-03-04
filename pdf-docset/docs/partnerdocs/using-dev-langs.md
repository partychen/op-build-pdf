# Using Dev Langs

The DevLangs metadata defines the content of the programming language selector and translates into BI data. Additionally the data is used to determine whether to hide or show specific code blocks.

## Defining Langs

You can define the dev langs on a per-page-basis by adding a `langs` property to your page metadata:

```YAML
langs:
  - csharp
  - vb
```

This enabes the effects discussed below for that page. Additionally, you can use your docfx.json file to configure this more broadly. Here's an excerpt from a docfx.json file that turns this on for a specific set of files:

```json
"fileMetadata": {
  ...
  "langs": {
    "api/**.yml": ["csharp", "vb", "cpp"]
  },
  ...
}
```

## The Toggle Effect

When a devLang is selected, different UI elements are hidden and then displayed, based upon their CSS class name.

### Toggle All Off

- **H1 span elements**. On a Managed Reference page, the content of the H1 is directly tied to the selected devLang.
- **code elements with devLang css and is togglable**. And show all parent `pre` elements.
- **div elements with devLang css and is togglable**

### Toggle Specific On

- **all elements with devLang css**
- **hide all pre elements with no visible children**

It may seem backwards, but `pre` elements are displayed first in order to give `code` elements a chance to be counted as visible.

`code` markdown and markdown extensions that are authored use the following format:

```html
<pre>
  <code></code>
</pre>
<pre>
  <code></code>
</pre>
```

`code` rendering written via templates may use the same `pre` parent element.

```html
<pre>
  <code></code>
  <code></code>
  <code></code>
</pre>
```

## No DevLangs Defined

No devlang selector is rendered and all code samples are displayed.

## One DevLang Defined

No devlang selector is rendered and all code samples are displayed.

## Multiple DevLang Defined

A devLang selector is rendered and code samples are hidden if their language is an option in the selector and it is not the currently selected language.

Language selection on page load is discovered in the following order:

1. User - Read from a cookie which is stored after they manually change the selector. Will change to default lang if user lang is not in the devLang selector.
1. Default - Set by content authors in metadata
1. First item - If no user or default, the first lang in the selector is selected.

## Default DevLang Meta Tag

This tag allows content authors to set the default selected devLang.

```json
"globalMetadata": {
		"defaultDevLang": "csharp"
}
```

## Display Lang Override

The values found in this meta tag will cause DocFX to only render an intersection of devLangs and displayLangs.

> [!IMPORTANT]
> Currently this meta tag is only observed during Managed Reference page generation.

The example below would only render csharp code samples.

```YAML
langs:
  - csharp
  - vb
```

```json
"globalMetadata": {
		"_displayLangs": ["csharp"]
}
```

## Managed Reference Properties

The following properties are dev_lang aware.

- name(.xx)
- nameWithType(.xx)
- fullName(.xx)
- modifiers(.xx)
- syntax.content(.xx)
- spec(.xx)