
# Deciding on publishing site and URL structure

## 1. URL Structure
Your URL will be defined by the domain/site where content gets published, locale, base URL path, and repo structure. 

 `http://{site}/{locale}/{BaseURL}{ContentPath}`
 
 Please follow [SEO guidelines](SEO-guidelines.md) AND ["the book of URL"](https://microsoft.sharepoint.com/teams/CE_CSI/Shared%20Documents/Forms/AllItems.aspx?id=%2Fteams%2FCE%5FCSI%2FShared%20Documents%2FCSI%20Spec%20Library%2FDocs%2FURL%20Rules%20for%20docs%2Emicrosoft%2Ecom%2Edocx&parent=%2Fteams%2FCE%5FCSI%2FShared%20Documents%2FCSI%20Spec%20Library%2FDocs&p=true) guidelines to make sure your URL complies with our requirements.

> [!IMPORTANT]
> Base URLs CANNOT be shared as of today. For example, if someone owns /productACME you cannot have another repo that has /productACME/folder1, /productACME/folder2, etc.... You would need to create a docset (even a dummy docset, for URL purposes and no real content) per "subproduct#" URL. 


### Parameters

- **Site** - The URL to the site that renders the content. It can be the URL for public site, internal testing or staging environment, or even localhost in local preview. It is not  related to git directory structure.
Sites supported
The first decision to make when publishing your content is to which site you are going to publish your content. The options are:
    1. MSDN
    2. TechNet
    3. VisualStudio
    4. DOCS
    5. Developer

- **Locale** - A string in {language}-{territory} format to indicate the locale of the content.

- **[Base URL](repo-creation-config.md)** - URL assigned to your content which maps to the docset in your repo.
    A docSet is a virtual grouping of document, like a portfolio in CAPS. Physically, it’s a folder in a Git repository. Each docset could be assigned with a publishing target site and base path, so all the contents within the docset would be published to the same destination. 

- **ContentPath** - [GIT repository](repo-creation-config.md) folder path of a topic plus the markdown file name without the MD extension.

> [!NOTE]
> Be aware that the fully qualified file name must be less than 260 characters, and the directory name must be less than 248 characters.

### 1.1 Example
https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/develop/make_mgmt_service 
- Site: msdn.microsoft.com
- Locale: en-us
- BaseURL: virtualization/hyperv_on_windows
- ContentPath: develop/make_mgmt_service(.md)

With this URL schema defined, content author and site management are given great flexibility in the layout of the content files in repo as well as rendering URLs. We recommend users to just using characters in the following whitelist to present a readable URL and avoid any potential SEO issue, ^[A-Z|a-z|0-9|\.|\(|\)|_|-|~]+$.

> [!Note]
> OPS infrastructure doesn't introduce extra restrictions on URL characters. Any character allowed by Git/file systems is also allowed by OPS system, with below special characters encoded by OPS in canonical_url:
":" / "/" / "?" / "#" / "[" / "]" / "@"
"!" / "$" / "&" / "'" / "(" / ")"/ "*" / "+" / "," / ";" / "=" .
> 
> In addtion, OPS hosting layer is case insensitive. For example, if a folder/file name is defined as upper case, it can been accessed by both upper case URL and lower case URL.

## 2. SEO guidelines
Make sure you review and follow the [SEO guidelines](SEO-guidelines.md) when deciding on the structure of your repo and creating folders and files.

## 2. Default URL
In order to avoid 404 page when navigating to the parent directory of an OP URL, you can use an index.md file in each folder. Here is what you need to do:

1. Create an index.md file in the folder you would like to control.
2. Add content to this file, keeping in mind that will be the default file users might see when the type only the parent directory.
3. Add this file to the TOC.md file, so when it displays, it shows the full TOC. 

Repeat the steps above for any folder you wuold like to have this functionality implemented.

### 2.1 Example
An example is available in this site. Go to to https://github.com/Microsoft/openpublishing-docs/tree/master/openpublishing/docs and see index.md and TOC.md. 

### 2.2 Redirection
In case you just want the default page to be a page which already exists, you can use the index.md file as a stub page for hosting your [Redirection](OPredirection.md). 

### 3 Remove Folder from URL
In some cases, you may want to have a different repository structure than your URL structure. OPS provides a flexible way for you to skip the folder name from your URL.

To achieve this, you would need to configure additional rule in docfx.json configuration file for your docset. For example, if you have folder *foo* in your repository which needs to be stripped out from the URL, you need to add the following configuration:
```
{
    "files":["*.md"],
    "src":"foo"
},
```
The logic behind is to "copy" src folder *foo* to the dest folder, and keep the relative path inside src folder as is. The above configuration specified src folder while dest folder is also specified in docfx.json as a required parameter.
For any folders you would like to strip out from the URL, nested or not, you would need to add a configuration for that foler. 
