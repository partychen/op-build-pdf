# Gauntlet VS Code Extension and Services (Dogfood)

![dogfood](media/gauntlet-dogfood.png)

The Gauntlet VS Code extension for OPS authoring provides Markdown authoring assistance to writers working in OPS and publishing to docs.microsoft.com. It includes several functions, including applying templates to new Markdown files, applying common formatting to strings, and inserting links, images, tokens, snippets, tables, and lists, as well as previewing content using the OPS build logic.

This topic describes the current Gauntlet dogfood version, 1.8.2, which contains new functionality not yet broadly released and is only available to a limited UAT group. If you would like to join, please email gauntletPM@microsoft.com.

New in 1.8.2:

- Metadata validation. You can check your files to confirm that required metadata is complete and values are valid, based on rules defined by the BI and SEO teams. See **Validation** in [Toolbar quick reference](#toolbar-quick-reference) below for how to validate your files in VS Code.  See [Gauntlet Validation Service](gauntlet-validation.md) for how to administer validation rules (business owners only).
- Insert bookmarks. See **Insert Link**, in [Toolbar quick reference](#toolbar-quick-reference) below.
- New OPS build-based preview. The new preview uses OPS build logic to more accurately render content. This preview also includes updates in real-time as you type, and if you scroll the preview window the authoring pane scrolls along with you.
- Various bug fixes and DCRs.

## Installation: Upgrade from previous UAT build

If you have a previously installed Gauntlet UAT build, such as 1.7.2, you will be prompted to upgrade to 1.7.5 when you open VS Code:

1. Agree to open the installer folder.
2. Double-click GauntletExtensionInstaller.exe.
3. The installer will uninstall the old version and install 1.8.2.

## Installation: First time install or upgrade from production release

Requires Windows on corpnet with Edge or IE:

1. If you haven't already, install [VS Code](https://code.visualstudio.com/Download).
2. If you have a previously installed production release of Gauntlet, such as 1.7.0, uninstall it first and reload VS Code.
3. Go to http://aka.ms/GauntletStage on Edge or IE.
4. Click **Download and Run the Installer**.
5. Save and run GauntletExtensionInstaller.exe.
6. If you see a security warning, select **More info**:

    ![windows-security-warning](media/windows-security-warning.PNG)

    ...then select **Run anyway**:

    ![windows-security-run-anyway](media/windows-security-run-anyway.PNG)

7. A command line will pop up, providing status as the extension installs.
8. When complete, you will see the new Gauntlet toolbar, including the validation checkmark, at the bottom of your VS Code window:

    ![gauntlet-toolbar](media/gauntlet-toolbar.png)

## Installation: Install manually from VSIX

Use this option to install on Mac or Linux, or on Windows with an unsupported browser. If your machine is not on corpnet, you will need to copy the VSIX manually, e.g. via thumb drive.

1. If you haven't already, install [VS Code](https://code.visualstudio.com/Download).
2. If you have a previously installed version of Gauntlet, uninstall it first.
3. Click the square icon on the left panel to open the **Extensions** menu.

    ![extension_icon](media/installation/extension_icon.png)

4. Click the three dots for **More** and select **Install from VSIX...**.

    ![extension_more](media/installation/extension_more.png)

5. Paste the path `\\dpspub\Gauntlet-Extension-Staging\gauntlet-1.8.2.vsix` into the **File name** box and click **Open**.
6. VS Code will install the extension and prompt you to restart.


## Prerequisites and assumptions

To effectively use the authoring extension, you must clone your entire repo to your local machine and keep it in sync. Functions such as link and image insertion are not reliable if the repo is out of sync.

## Known issues

- The new preview creates a local environment that can leave a process, DfMHttpService, running in the background, preventing full uninstallation. If you need to uninstall Gauntlet and get strange errors, this is likely the cause. Just close and reopen VS Code and uninstallation should succeed.
- The new preview renders some items, such as alerts, includes, code, and images, inconsistently. Sometimes this is because the environment is still building in the background, sometimes if you edit the text the items stop previewing correctly. Closing and reopening the preview may fix the issue. These bugs are under investigation and will be fixed before the new preview releases to production - let us know if you find other issues!
- Hotkeys may conflict with other applications. We have chosen an unusual convention, `Ctrl+Shift+Alt`, to minimize conflicts - but we cannot predict what hotkeys may be assigned by other applications installed on your machine. If a hotkey does not work as documented, it probably means you have a conflict. To assign a different hotkey, see [Customizing Shortcuts](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) in the VS Code docs. You can also do this if you just find our convention too clumsy!

## Toolbar quick reference

|Tool Bar Icon |Description  |
|---------|---------|
|![CreateFile](media/ExtensionIcons/CreateFile.png)| **Create New File** - Use to create a new unsaved document tab, that you can author directly or copy a template into.  Hotkey: `Ctrl+Shift+Alt+N`.  |
|![ApplyTemplate](media/ExtensionIcons/ApplyTemplate.png)|**Apply Template** - Use to apply a template, such as the standard docs.microsoft.com metadata template.  If your document already has content the template will be inserted in place. Hotkey: `Ctrl+Shif+Alt+M`. For more information, see [Gauntlet Template Service](gauntlet-templates.md). | 
|![Bold](media/ExtensionIcons/Bold.png)|**Bold Text** - Use to bold a string or block of text. Hotkey `Ctrl+Shift+Alt+B`. | 
|![Italic](media/ExtensionIcons/Italic.png)|**Italic Text** - Use to style a string or block of text as italic. Hotkey: `Ctrl+Shift+Alt+I`. | 
|![Code](media/ExtensionIcons/Code.png) |**Code** - Use to style a string or block of text as code. If you select a line or less of text, then click the button or use the `Ctrl+Shift+Alt+C` hotkey, the Gauntlet extension will style the string as code inline. If you select more than one line, it will be styled as fenced code. |
|![Alert](media/ExtensionIcons/Alert.png)|**Insert Alert** - Use to insert a note, warning, important, or tip. After clicking the button, choose the alert type from the quick pick menu. If you need to add additional paragraphs to your alert, be sure to add a `>` after each line break, including the blank line between paragraphs. Hotkey: `Ctrl+Shift+Alt+1`.|
|![OrderedList](media/ExtensionIcons/NumberedList.png)|**Insert Numbered List** - Use to insert an ordered (numbered) list. Hotkey: `Ctrl+Shift+Alt+O`.| 
|![UnorderedList](media/ExtensionIcons/BulletedList.png) |**Insert Bulleted List** - Use to insert an unordered (bulleted) list. Hotkey: `Ctrl+Shift+Alt+U`.|
|![InsertTable](media/ExtensionIcons/InsertTable.png)|**Insert Table** - Use to insert a table. The number of rows and columns are entered in `C:R` format, for example `3:5` indicates a table with three columns and five rows. Per content guidelines, tables inserted via Gauntlet are limited to a maximum of four columns and fewer than one hundred rows, although you can add more manually. Hotkey: `Ctrl+Shift+Alt+T`.| 
|![InsertLink](media/ExtensionIcons/InsertLink.png)|**Insert Link** - In your Markdown file, type the link text and select it, or put your cursor where you want to add a link. Click the button or use the `Ctrl+Shift+Alt+L` hotkey to open the quick pick menu, then select **External**, **Internal**, **Bookmark in this file**, or **Bookmark in another file**. <br><br>For internal relative links, choose the link target from the quick pick menu that appears. You can either scroll through the list or start typing in the text box to filter search results.<br><br> For bookmarks in the same topic, choose from a the list of headings in the topic. <br><br>For bookmarks in another topic, first find the topic you want to link to, just like inserting an internal relative link, then choose the heading in that topic.<br><br> For external links, type or paste the full URI, including `http://` or `https://`. |
|![InsertImage](media/ExtensionIcons/InsertImage.png)|**Insert Image** - Type alt text and select it or put your cursor where you want to insert art. Press the button or use the `Ctrl+Shift+Alt+ A` hotkey, then choose the link target from the quick pick menu that appears. You can either scroll through the list or start typing in the text box to filter search results.  |
|![InsertInclude](media/ExtensionIcons/InsertInclude.png)|**Insert Include** - Use to insert included files (tokens). Hotkey: `Ctrl+Shift+Alt+E`. | 
|![InsertSnippet](media/ExtensionIcons/InsertSnippet.png)|**Insert Snippet** - Use to insert a code snippet. Hotkey: `Ctrl+Shifft+Alt+S`. | 
|![Preview](media/ExtensionIcons/PreviewFile.png) |**Preview Content** - Provides more accurate Markdown preview based on the OPS build logic. Hotkey: `Ctrl+Shift+Alt+P`. | 
|![Validate](media/ExtensionIcons/Validate.png)|**Validate** - Validates the current file against the ruleset associated with your repo. Hotkey: `Ctrl+Shift+Alt+V`.|
|![Feedback](media/ExtensionIcons/Feedback.png)|**File Bug or Feature** - You can now submit feedback directly from the Gauntlet toolbar! Click to submit your feedback through VSTS. The Gauntlet team will triage your bug, DCR, or feature request for possible implementation in a future release. Hotkey: `Ctrl+Shift+Alt+F`.|

## Gauntlet services

The Gauntlet VS Code extension is the front-end to services that help manage and validate content. In general, only content admins will need to interact with Gauntlet outside of VS Code; for more information about using and administering these services, see:

- [Template Service](gauntlet-templates.md)
- [Validation Service](gauntlet-validation.md)
- [PR Merger](prmerger-overview.md)




