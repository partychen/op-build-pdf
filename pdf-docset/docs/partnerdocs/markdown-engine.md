# G​FM and ​CommonMark

GitHub GFM switched to use [CommonMarkd](https://githubengineering.com/a-formal-spec-for-github-markdown/) on 2017/3/14.

We have found some major syntax changes between old GFM and Common Markdown (new GFM).

## Syntax changes

### 1. Heading

In old GFM, `#title` is a valid heading.

In new GFM, `#title` is invalid: at least *one space* is required after `#`, e.g. `#{space}title`.

### 2. List

#### 2.1 Indentation

In old GFM, indentation is not sensitive. Below is a valid list

```md
1.{space}a

{space}b
```

which renders to

```html
1. a
   b
```

In new GFM, indentation is sensitive, and above md renders to

```html
1. a
b
```

To move `b` into list, we need add *same amount of indentation* with `a`.

```md
1.{space}a

{space}{space}{space}b
2.{space}{space}c

{space}{space}{space}{space}d
3.{space}e

{space}{space}{space}f
```

#### 2.2 Start index

In old GFM, ordered list always start with 1 in rendered result.

In new GFM, ordered list can start with any number and the starting number would be the first item in the list.

```md
0. a
0. b
```

renders to

```html
0. a
1. b
```

```md
100. a
99. b
```

renders to

```html
100. a
101. b
```

#### 2.3 Stop rule

In old GFM, list is stopped by two new lines followed by any text without indentation:

```md
1. a

b
```

In new GFM, list is stopped by following criteria:

##### Rule 1: After an empty line, without *enough* indentation

```md
1. a

{space}b
```

##### Rule 2: After one new line, without enough indent and content matches some block rules (heading, block quote, list, hr)

```md
1. a
# b
```

### 3. Stop rule for block quote

In old GFM, block quote is stopped by two new lines.

In new GFM, block quote is stopped either by two new lines, or by one new line with following content matching some block rules (heading, block quote, list, hr).

```md
> a
- b
```

### 4. Definition

In old GFM, definition can write in top level, i.e. cannot write definition in list.

In new GFM, definition can write in list.

```md
1. [a]: b
```

renders to

```html
1.
```

## Switch markdown-engine in Open Publish

You can switch markdown-engine per docset.

### How to switch markdown-engine
1. Open your docset folder
2. Open the `docfx.json`
3. Find `build` property
4. Append property `markdownEngineName`
   
   Name of markdown engine (default is `dfm`):
   * `dfm-2.13`: old markdown engine
   * `dfm-2.15`: the new markdown engine (following common mark)
   * `dfm`: the default markdown engine (same as `dfm-2.13` now)
   * `dfm-latest`: the latest markdown engine (same as `dfm-2.15` now)
   
   For example:
   ```json
   "markdownEngineName": "dfm-latest"
   ```
   
   > [!Note]
   > For docsets in Content.VS repo, please set a different markdown engine name:
   >
   > * `opdfm`: the default markdown engine (using old syntax now)
   >
   > * `opdfm-latest`: the latest markdown engine (using new syntax now)
   >

### How to check markdown content is correct for new markdown engine
1. Clone [tool repo](https://github.com/vwxyzh/MarkdownVariationBin)
2. Run `MarkdownVariation.exe docset_folder **.md > logfile`

   This tool compares the syntax tree between two versions of markdown engine and lists the potential differences.

3. Check log file

   > [!Tip]
   > The log file contains following content: `"name": "64>78>ol"`
   > it is in format: `start line number > end line number > element name`
   
4. Open markdown files, go to the different line, then validate the changes in GitHub preview, if wrong, fix them.

### How to migrate markdown content to CommonMark by tool
1. Clone [tool repo](https://github.com/vwxyzh/MarkdownMigrateBin)
2. Run tool
   * Single file:

     ```
     MarkdownMigrate.exe input.md output.md
     ```
   * Batch:

     ```
     MarkdownMigrate.exe -i < file.list
     ```
     file.list is a file with content each line is a markdown file name.
3. Verify the result of markdown files.
