# OPS Custom Domain

> [!IMPORTANT]
> As a team, we have a policy to *not* support internal teams as our team has a laser-focus on building a great solution for customers. Beyond having a clear focus, there are a few reasons we can’t including cost, support, and unique-to-Microsoft features (LCA requirements for restricting content, tagging content as MBI/HBI, etc) that don’t exist on docs. 

> Our longer-term solution would be to provide Docs-as-a-service on Azure for customers (and therefore internal teams), but we still need to figure out the best way to do this.  

> Please contact Dan Fernandez if you have any questions.

## Main contacts
* Zhen Jiao - Custom domain engineer lead
* Tianqi Zhang - Custom domain engineer
* Zhiliang Xu - Backend and rendering engineer lead
* Sandra Aldana - PM

## Introduction

The following documentation is for teams who want to publish documentation using OPS to their own custom domain. 

A custom domain is a site that can be used either for internal or external customer access and that is setup, maintained, service, etc. by the content owner and not by the VSC team. 

> [!NOTE]
> Currently the major customers of OPS inside Microsoft are still focusing on large web sites like MSDN or docs.microsoft.com. For custom domain, we have onboarded 2 sites in OPS, but still seeking to see how many others will be need. If this important enough, we can make sure we have provided all the key features, to make sure our investment can benefit for more teams. If you have any comments or feedback for this, feel free to let us know.

> [!IMPORTANT]
> At this moment, we will not be able to add additional functionality to support your custom domain needs shall you have any. It is TBD when we can invest on additional functionality.

## Requirements from OPS
### Source
* Most of the requirements and functionality are the same than if you were publishing to one of VSC domains (MSDN, TechNet, VisualStudio, DOCS). So we recommend you get familiar with the [OPS user documentation](https://opsdocs.azurewebsites.net/en-us/opsdocs/index?branch=master). 
* Files need to be stored in either GitHub or VSTS
* Files need to be in Markdown or YML.
* OPS uses [docfx](https://github.com/dotnet/docfx) as one of their plugin components. OPS converts the MD/YML files to HTML and copies them to the Azure websites blob storage. OPS copies over images to the website services. 

### Site
* Site to be hosted on Azure websites
* According to CELA, your site should have a copyright. [Here](https://microsoft.sharepoint.com/sites/LCAWeb/Home/Copyrights-Trademarks-and-Patents/Copyrights/Legal-Notices) is the information on how to create a copyright notice. 
* Tell us whether you would like us to use OPS built-in AAD. 
    * If yes, your site will be considered internal site. You can use internal features such as branch selector. The site will be only available to coprnet accounts. 
    * If not, your site will be considered a production site. This is recommende when you need to grant access to users outside Microsoft to the site. In that case, please activate AAD from the Azure portal. Internal features such as branch selector are no available. If you want to use some internal features like branch selector, you’ll have to create a “staging” site which uses OPS AAD.

## Onboarding Steps

1. Partner - Grant admin access to VSC (we will provide you the accounts) to provision your repo and share repo URL. 
    *Admin permission can be removed after provision is done.
2. Partner - Provide the Azure subscription you are hosting the webapp.
3. VSC - Deploy our hosting bits to partner's Azure subscription.
4. Partner - Indicate what kind of theme/template you want to use for the site. Currently we support 1: [docs.microsoft.com  (used in OPS documentation)](https://opsdocs.azurewebsites.net/en-us/opsdocs/?branch=master).
5. VSC - Provision the repo to VSC Azure websites as a test.
6. VSC - Share rendering site with partner.
7. Partner - Validate content and signs off.
8. VSC - Provision the repo to publish to Partner's blob storage via backend
    	* Deploy OPS rendering bits to partner's Azure website, and configure it to read content from OPS. Benefits: 
            * It supports some hosting related requirements like routing, 404 pages, 301 redirecting, multiple locales
            * It supports to auto generate the sitemap for SEO

> [!NOTE]
> OPS zips the build outputs and stores them in blob storage managed by OPS. Currently the blob storing the build output is public. Although the blobs are public, their URLss are hidden, only known to rendering bits. And the blob containers are private. So it’s very unlikely that an outside user can “guess” such a URL. Even they do have the urls, all they can do is read.

## Out of the scope functionality
* OPS will not copy other binaries other than images (such as videos, Office documents, etc.) to the Azure websites blob storage.
* AAD-based authorization is not enabled. It can be done via configuration changes in the Azure portal.
* Additional template support. There are still 3 options:
    1. Work with Duncan Mackenzie's team (who is the owner of docs.msft theme and template) to add support for more themes.
    2. Work with Duncan's team to add some logic in the current theme to turn on your custom header&footer. This is the approach currently used to switch between default theme and Azure theme on docs.msft.
    3. Add your own script in your contents to tweak the header&footer.
* Current template does not support Universal Header and Footer (UHF). Request for that support is in [Feature 661223: Support UHF for Docs](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems/edit/661223).

## Visual Workflow
`Zhen, Tianqi, please add here a visual of how OPS interacts with the GitHub repo, our websites blob storage, and the partner's custom domain.`

