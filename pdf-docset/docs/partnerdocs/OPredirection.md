# Redirection options

## 1. Moving from MTPS to OPS
Scenario: When you move from MTPS to OPS.

See [MTPS redirection](paveover-mtps-content.md)

## 2. Topic level redirection in OPS
Scenario: A file or subset of files are renamed. 
 
Open Publishing supports redirection at the topic level. You need to keep the former file (File A) in your repo and create a new file with the new name (File B). In case you would like to eventually remove the original file (File A), please refer to [master redirection file](#3-master-redirection-file).

Write a [metadata](metadata.md) with name "redirect_url" in the yaml header, then the page will redirect to the topic or page specified.
Note that the target URL needs to be either a absolute URL/path or the path relative to the site root. 

Cases

1. A full/absolute URL

    ```
    ---
    redirect_url: https://msdn.microsoft.com/virtualization/windowscontainers/
    ---
    ```
    
    Or
    
    ```
    ---
    redirect_url: https://docs.microsoft.com/azure/virtual-machines/windows/
    ---
    ```
2. A partial URL without the domain, which implies that the target URL is within the same domain as the source URL, pointing to a published folder from OPS (`windowscontainers` is the folder). In this case, the index page under the specified folder would be used as redirection target.

    ```
    ---
    redirect_url: /virtualization/windowscontainers/
    ---
    ```
    
    Or
        
    ```
    ---
    redirect_url: /azure/virtual-machines/windows/
    ---
    ```
   
3. A partial URL without the domain, that points to a folder and file name that's published with OPS. Leave off the file name extension (e.g. .md). In these examples, `getting-started` and `virtual-machines-windows-hero-tutorial` are the file names.

    ```
    ---
    redirect_url: /virtualization/windowscontainers/getting-started
    ---
    ```
    Or
    ```
    ---
    redirect_url: /azure/virtual-machines/windows/virtual-machines-windows-hero-tutorial
    ---
    ```
    
When a OPS page is redirected to another OPS page, OPS provides a mechanism to allow carrying over "ms.documentid" to the target OPS page by meta "redirect_document_id". This could be used when user wants to transfer the data collected from the source page to the target one. For example, the redirected-out page can be specified as following: 

```
---
redirect_url: /virtualization/windowscontainers/ 
redirect_document_id: TRUE 
---
```
Or

```
---
redirect_url:  /azure/virtual-machines/windows/
redirect_document_id: TRUE 
---
```

> [!WARNING]
> Mapping a redirect_document_ID across docsets is NOT supported at this time.

## 3. Master Redirection File
In majority of the cases, user would like to remove the source file once the redirection is activated. We provide the users a way to maintain those redirections in a centralized file without the need of keeping the obsoleted files.  

The master redirection file is a JSON file located and consists of a list of redirection pairs.  
* File name: *.openpublishing.redirection.json*
* File path: *at the repository root*


|Value  |Explanation  |Required or Optional  |
|---------|---------|---------|
|source_path   |  The relative file path to the repository root (with file extension). Remember the master redirection file is located at the root of the repo, so you need to include the docset name as part of the path to the file. | Required |
|redirect_url | Target URL to redirect to. It can be either an absolute url or a url relative to the root of the same site where the source was published to. Thus, you need to start with "/" and add the base URL path followed by the rest of the target URL | Required |
|redirect_document_id | Indicates whether you would like to keep the document_id or not from the previous file. It is a boolean. If omitted, value is set to false. | Required |

> [!NOTE]
> The files referenced as source in the master redirection file should not exist in the Git repository. So if a redirection needs to be managed in the master redirection file, the original file must be removed.  

Example: 
```
{ 
  "redirections": [ 
    {   
        "source_path": "abc/def.md", 
        "redirect_url": "/abc/xyz", 
        "redirect_document_id": true 
    }, 
    { 
        "source_path": "abc/ghi.md",
        "redirect_url": "http://www.opq.com/uvw", 
        "redirect_document_id": false 
    } 
  ] 
} 

```

We also build some validations around the redirection rules, which includes

|Rules   |Error or Warning   |Examples   |
|---|---|---|
|[within repo] source_path should not be null or empty; otherwise result the following error. (source_path for redirect_url 'xxx' is null or empty.)   |Error   |"source_path": null   |
|[within repo] source_path should not be above repository root path; otherwise result the following error. (source_path 'xxx.md' is above the root path 'yyy'.)   |Error   |"source_path": /a/b.md   |
|[within repo] redirect_url should not be null or empty; otherwise result the following error. (redirect_url for source_path 'xxx' is null or empty.)   |Error   |"redirect_url": null   |
|[within repo] redirect_url should not be relative path; otherwise result error|Error   |"redirect_url": c/d   |
|[within repo] There should not be duplicated entries in mapping files; otherwise result the following error. (There are duplicated entries for source_path 'xxx.md' in redirection mapping file.)   |Error   |         |
|[within repo] If the redirection file still exists, result the following warning. (xxx.md would be overwritten by redirection rule configured in master redirection file .openpublishing.redirection.json. Please remove the original file to resolve this warning)   |Warning   |         |
|[within docset, and all redirect_document_id = true] Multiple topics redirect to same page, pick up first redirect-from page (in order of relative path in docset) to generate document id|Warning   |A.md, B.md, C.md all redirect to D.md: set document id of D.md to A.md         |
|[within docset, and all redirect_document_id = true] Recursive redirection    |Error   |A.md -> B.md -> A.md or A.md -> A.md         |
|[within docset] *not supported yet* multi-hoop redirection    |Warning   |A.md -> B.md -> c.md        |

The redirection rule is not locale specific, one rule configured in English repository would be automatically applied to all other locales. The only thing needs to be pointed out here is, after the redirection, OPS would select the user's default locale to display the redirection target documentation. The user's default locale is determined by cookie (which is set by locale picker) and then browser language setting. 

## 4. DocSet and Folder Level Redirection
Those levels of redirection would be managed on Network Layer (Akamai or similiar) to obtain the best performance. Please follow the steps described in below section to set up those redirection rules once needed. 

## 5. Site Level Redirection 
<a name="SiteRedirection"></a>

> [!NOTE]
> Applies to: docs.microsoft.com, MSDN, TN, and VisualStudio.com content published with OPS.

Usages: 
* For Docs, When both the endpoints have to be in place to stop bad end-user experience until the traffic to older endpoints reduces to get the redirection rule removed from Akamai. 
* For MSDN/TN and VS.com we do not do redirection from Akamai, but can write a ARR rule for the same depending on the request.

Scenarios: 
1. Updates on the base URL in OPS
2. Folder renaming in the Git repo other than the docset folder

`Please open the request 5 business days in advance.`  

Steps:
1. Open a request in [SiteHelp portal](http://aka.ms/sitehelp).
2. Tag the request with `Redirection` tag.
3. Include the following information:
    * Current and New URLs
    * Date and time when the redirection needs to take place:

> [!IMPORTANT]
> Because this work is done in Redmond, this redirection work needs to be done ***Monday to Friday, 9 am - 6 pm Redmond***.
> If you absolutely need a redirection done over the weekend or outside those hours, in addition to the ticket, please contact [Guang-ang Wu](mailto:guangw@microsoft.com) at least 5 business days in advance.


### Ticket example
````
Reason: We are rebranding our product. As a result, we need docset renaming and site-level redirection.
Current URL: docs.microsoft.com/enterprise-mobility 
Target URL:  docs.microsoft.com/enterprise-mobility-security
Date and time to go live: October 16, 5pm
````

### What you can expect after the ticket is opened:
* APEX Engineering will contact you to acknowledge your request and follow up on any questions.
* APEX Engineering will ask you to sign off on the validation on stage (VSC will send you instruction on how to do it).

    
* `You will need to be available at the day and time of the redirection.` 
* Content will need to be published for all locales live under the new URLs before the redirection. This is to ensure the target endpoints is live and doesn’t throw non 200 to avoid bad end user experience.
    * If you are renaming the base URL, VSC will do that for you and publish your content live. ***Note that this change affects all locales.***
    * If you are just renaming a folder, ***content will need to go live before we apply the redirection.***

> [!IMPORTANT]
> Due to the redirection activation time in production varies, we may expect a very small % of users getting 404s when they try to load the redirecting URLs from their bookmark during the timeframe when the activation is in progress.
