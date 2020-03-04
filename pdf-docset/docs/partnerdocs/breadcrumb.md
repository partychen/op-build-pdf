---
author: hexiaokai
---
#Breadcrumb 

Breadcrumb is a very common navigation component, it usually appears at the top of the page and enables the user to navigate to higher-level document collections. Also, the breadcrumb offers users an idea about under which part of the site they are currently viewing. In OPS, breadcrumb is very similar to a TOC, where the hierarchy is specified in a separated file in a structured way, with other pages just referencing the breadcrumb file and rendering on the page. Here is a sample of how a breadcrumb looks like:
![Breadcrumb sample](../images/breadcrumbsample.png)

##What does the breadcrumb source file look like
In OPS, breadcrumb data is put into either a toc.yml file. This is a YAML format file and the breadcrumb data is organized in a parent-child relationship. This relation specifies a logical navigation path for the site. For example:

```md
- name: Enterprise Mobility
  tocHref: /EM/
  topicHref: /EM/index
  items:
  - name: Solutions
    tocHref: /EM/Solutions/
    topicHref: /EM/Solutions/byod-design-considerations-guide
  - name: Advanced Threat Analytics
    tocHref: /ATA/
    topicHref: /ATA/index
    items:
      - name: Understand and explore
        tocHref: /ATA/Understand/
        topicHref: /ATA/understand/ata-understand-and-explore
      - name: Plan and design 
        tocHref: /ATA/PlanDesign/
        topicHref: /ATA/plandesign/ata-plan-and-design
  - name: Intune
    tocHref: /InTune/
    topicHref: /InTune/index
    items:
      - name: Understand and explore
        tocHref: /Intune/Understand/
        topicHref: /Intune/understand-explore/ways-to-do-enterprise-mobility
      - name: Deploy and use
        topicHref: /Intune/DeployUse/learn-how-to-deploy-a-solution-for-protecting-company-email-and-documents
``` 

The above example contains the following breadcrumb paths:
    * `Enterprise Mobility`    
    * `Enterprise Mobility -> Solutions`
    * `Enterprise Mobility -> Advanced Threat Analytics`
    * `Enterprise Mobility -> Advanced Threat Analytics -> Understand and explore`
    * `Enterprise Mobility -> Advanced Threat Analytics -> Plan and Design`
    * `Enterprise Mobility -> InTune`
    * `Enterprise Mobility -> InTune -> Understand and explore`

There are three types of input in the yaml file. **The three fields are mandatory**:
* `name` - The display text that shows up on the breadcrumb. 
* `tocHref` (formelly `href`) - This is the URL part to detect which breadcrumb node to match. 
  * To match and show the correct breadcrumb entry, you must have a TOC file directly under the path you're referring to, so the topics referenced by that toc would have the particular breadcrumb entry highlighted.
  * It always have to start with a forward slash `/`.
  * It can be:
    * The relative path from the breadcrumb file to the folder where the TOC is located in the same docset.
    * The absolute path from the site domain. Then it needs to start with the base URL of your docset.

  * It always have to end with a forward slash `/`.
  
    > [!NOTE]
    > If you have only 1 TOC file for your entire docset, the breadcrumb won't help navigate inside your docset, but you can use it to connect multiple docsets. If you already have separated TOC files for your docset, you can use a breadcrumb to connect those separated TOCs together.

    > [!IMPORTANT]
    > Breadcrumbs will not work with nested TOCs. 
* `topicHref` (formelly `homepage`) - This is the URL that leads to a landing topic after user clicks on the breadcrumb link.
  * It always have to start with a forward slash `/`.
  * It should be the absolute path from the site domain to the file to display, .i.e. it needs to start with the base URL of your docset.
  * The file should not contain any extension

##Where to put the breadcrumb source file
The breadcrumb source file (toc.yml) can be put in any folder within any *provisioned* docset in your repo, in any folder in a *provisioned* docset in the same repo, or in any folder in a *provisioned* docset in a different OPS repo. That is because breadcrumb is usually a global navigation concept and links different docsets and repos.  Note that in this case, all the repos need to publish to the same domain. 

For example, if you put the toc.yml file under the root folder of docset "EnterpriseMobility", whose base URL is "/EM/", after building the docset, you can verify the built breadcrumb data via `http://{SiteDomain}/EM/toc.json`.  

The only restriction is that you do not put the toc.yml file in the same folder than the TOC.md file. By doing so, the build system will pick up only the toc.yml file and the TOC.md file will not be picked. 

For example, if you want to put the toc.yml file it in a docset that already has a TOC.md in root folder, one solution is to put the toc.yml file in a subfolder, say `breadcrumb`.

##How to include breadcrumb source file for build
In order to reference the breadcrumb source file, you need to update the **docfx.json** in all the docsets that are displaying the breadcrumb. This needs to be done as global metadata, so that current docset will pull breadcrumb data from specified location. 

We have the breadcrumb in `/EM/breadcrumb/toc.yml` file in our repo but in the "EnterpriseMobility" docset. We are updating the docfx.json file in the "InTune" docset... 

We need to indicate the build system that we need to include the YAML file in the build. Thus, **ONLY** in the docset where the toc.yml file is placed, update the docfx.json file. You need to add the .yml extension in the `files` section as follows.

```json
     "content":
      [
        {
          "files": ["**/**.md", 
                    "**/**.yml"],
          "exclude": ["**/obj/**"]
        }
      ],
```

Add the `breadcrumb_path` line in the form `/{base URL of the docset}/{breadcrumb folder in the docset}/toc.json`. Following our example, it would be "/EM/breadcrumb/toc.json".

```json
    "globalMetadata": {
      "layout": "Conceptual",
      "breadcrumb_path": "/EM/breadcrumb/toc.json",
      "ms.locale": "en-us"
    }
```

>[!IMPORTANT]
>When using a hard-coded path, specify the toc.yml file extension as '.json' regardless of the **actual** extension of the input breadcrumb toc.yml file.

As you can see, we support relative path for breadcrumb source file, and it's always related to the root of docset. However, you couldn't put the toc.yml file under other OP provisioned docset using relative path.


Also, if toc.yml file is under current provisioned docset, you can use the relative path in docfx.json, from the docset folder. However, we advice you always you use the absolute path so you can use the same syntax for all your docsets. 

```json
    "globalMetadata": {
      "layout": "Conceptual",
      "breadcrumb_path": "/breadcrumb/toc.yml",
      "ms.locale": "en-us"
    }
```

##Why the breadcrumb does not show on my page?
1. Please view the source of a published page to check if there is `breadcrumb_path` metadata. If yes, check if the path is the one expected.
2. If there is no breadcrumb_path metadata, please check if the breadcrumb_path is added as global_metadata in docfx.json in your repo.
4. Check that the breadcrumb is published. For example, if you put the toc.yml file under the a "breadcrumb" folder at the root of docset "EnterpriseMobility", whose base URL is "/EM/", after building the docset, you can verify the built breadcrumb data via `http://{SiteDomain}/EM/toc.json`. Make sure that path matches with what you have in #1.  
3. If everything above is correct, please double-check the breadcrumb source file to see if the href is set correctly. Also check the build report to ensure that there are not structure problems with the breadcrumb.
5. Check if the breadcrumb source file has been included for build in docfx.json file: look for "**/**.yml" under the `files` section.
6. Report issue on [SiteHelp portal](http://aka.ms/sitehelp).