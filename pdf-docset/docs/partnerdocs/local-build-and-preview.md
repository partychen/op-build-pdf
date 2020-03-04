# Local builds and preview
Open Publishing allows you to build your content locally to detect any potential error (like broken links), as well as preview your content locally for validation. 


## 1. <a name="local-build"></a>Local validation build 
Local build only runs build command to validate all the files build correctly. 
* Step 1: Clone your repo to your local machine. You can use Visual Studio or [GitHub Desktop](https://desktop.github.com/).
* Step 2: Run the Local validation build command
    * From Visual Studio, 
        * Right-click on the cloned repo and click on **Open command prompt**.
        * Run the command `powershell .openpublishing.build.ps1`    
    * From GitHub Desktop, 
        * Right-click on the repo and click on **Open in Git Shell**.
        * Run the command `.\.openpublishing.build.ps1`

> [!IMPORTANT]
> If you get the warning "Api rate limit exceeded", please append one more parameter to give your access toekn after the command above.
> For example:
> 
> From Visual Studio: `powershell .openpublishing.build.ps1 -parameters:"_op_accessToken=<your personal access token here>"`
> 
> From GitHub Desktop: `.\.openpublishing.build.ps1 -parameters:"_op_accessToken=<your personal access token here>"`

Below table shows all optional arguments supported by Open Publishing tool. You may specify additional arguments separated by `;` as below

`.openpublishing.build.ps1 -parameters:"{arg1}={value1};{arg2}={value2};...;{argN}={valueN}"`.

| Argument | Setting | Example |
| -------- | ------- | ------- |
| _op_accessToken | The Git access token to access Git data. [[GitHub]](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) [[VSTS]](https://www.visualstudio.com/en-us/get-started/setup/use-personal-access-tokens-to-authenticate)  <ul><li>Optional if the Git repo is public.</li><li>Required if the Git repo is private.</li></ul> | `-parameters:"_op_accessToken={your access token}" ` | 
| Targets | <ul><li>build<br/><p>Build target will get latest build scripts and bits to do content build.</p></li><li>serve<br/><p>Besides build, it will host local iis server to allow you to vist page with browser.</p></li><li>init<br/><p>Prepare environment for your build, such cloning template, restoring nuget packages and other network operation.</p></li><li>localbuild</li><br/><p>Do local build without access the network. Before calling this, you must call any one of the above targets at first.</p><li>generatePdf</li><br/><p>Use this target to build out content, and to generate the pdf.</p><li>generateIntellisense</li><br/><p>Use this target to generate intellisense.</p></ul> | `-parameters:"Targets=build"` |

> [!TIP]
> Use the following command to accelerate your local build speed.
> 1. `powershell ".\.openpublishing.build.ps1 -parameters:'_op_accessToken=<your_access_token>;Targets=Init'"`
> 2. `powershell ".\.openpublishing.build.ps1 -parameters:'_op_accessToken=<your_access_token>;Targets=LocalBuild'"`
> 3. `powershell ".\.openpublishing.build.ps1 -parameters:'_op_accessToken=<your_access_token>;Targets=GeneratePdf'"`
> 4. `powershell ".\.openpublishing.build.ps1 -parameters:'_op_accessToken=<your_access_token>;Targets=GenerateIntellisense'"`
> 5. If you meet the scripts running issue with powershell policy restricted, please run "Set-ExecutionPolicy RemoteSigned" under admin mode to remove that restriction.

* Step 3: Look at the report. The report is inside the local folder where you cloned your repo, under “./log/report.txt”. Fix any errors that you might have. Run the command again to validate you are error free. 

## 2. Local preview
In addition to do build validation, local preview validates that the content and TOC look as you expect. 

* Step 1: Clone your repo to your local machine. You can use Visual Studio or [GitHub Desktop](https://desktop.github.com/).
* Step 2: Run the local preview commands:
    * From Visual Studio, 
        * Right-click on the cloned repo and click on **Open command prompt**.
        * If you are working on content for docs.microsoft.com, run this command `git submodule update --init`. This downloads the docs.microsoft.com themes to your machine.
        * Run the command `powershell .openpublishing.build.ps1 -parameters:targets=serve`    
    * From GitHub Desktop, 
        * Right-click on the repo and click on **Open in Git Shell**.
        * If you are working on content for docs.microsoft.com, run this command `git submodule update --init`. This downloads the docs.microsoft.com themes to your machine.
        * Run the command `.\.openpublishing.build.ps1 -parameters:targets=serve`
* Step 3: Look at the report. The report is inside the local folder where you cloned your repo, under “./log/report.txt”. Fix any errors that you might have. Run the command again to validate you are error free. Once you do not have any errors, you will be able to see the preview. 
* Step 4: Open http://localhost:8080 to see your content locally.

Note that any changes that you make after this point, are not going to be reflected in the local web site. You will need to close the command prompt window that popped up and run the local preview command again.

## 3. <a name="local-pdf"></a>Local PDF output
Follow same steps as [local validation build](#local-build) and make sure you turn on the build of PDF in [publish configuration](publish-configuration.md#publish-config-need_generate_pdf).
> [!TIP]
> Use the following command.
> `powershell ".\.openpublishing.build.ps1 -parameters:'_op_accessToken=<your_access_token>;Targets=GeneratePdf'"`

After run generate pdf target, go to your repository folder, the generated pdf(s) are under `_site` folder. Each toc under docset will be built into one PDF named by `{docset name}.{locale}.{toc_asset_id}.pdf`.

## 4. <a name="local-intellisense"></a>Local Intellisense output
Follow same steps as [local validation build](#local-build) and make sure you turn on the build of Intellisense in [publish configuration](publish-configuration.md#publish-config-need_generate_intellisense).
> [!TIP]
> Use the following command.
> `powershell ".\.openpublishing.build.ps1 -parameters:'_op_accessToken=<your_access_token>;Targets=GenerateIntellisense'"`

After local build, go to your repository folder, the generated intellisense file(s) are under `_site/_intellisense` folder. Each docset will be built into one folder named by `{docset name}`.

