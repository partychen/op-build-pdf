# Going live
[!include[Going live](../includes/goinglive.md)]

## <a name="MergeMasterToLive"> </a>Merging master branch to live branch
Merging master to live branch can be done directly in GitHub or VSTS. However, APEX engineering team has created a plug in to facilitate the work, specially when localization needs to do this for multiple locales.

To install the plug in:
1. Go to [OPS portal](https://OPS).
2. Click on ***Plug ins***. The plug in you want is ***BranchMerger*. 
3. Click on ***Install.***

To use the plug in once installed:
1. Go to [OPS portal](https://OPS).
2. Go to the docset you would like to do the merge.
3. You will see the plug in options at the bottom of the page, under ***Merge master to live***.
4. Select the locales you would like to do the merge.
5. You can see in the table what files are different. You can click on the link to see the difference in GitHub or VSTS.
5. Choose whether you would like to ***Merge with pull request*** or ***Merge with pushing directly***, and click on the button.

> [!NOTE]
> This merge does not affect the setting on the GOTO live flag. 
