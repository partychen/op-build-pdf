 ## Request a new locale
OPS will only allow you to add locales for those locales we support in our end points. This is to ensure that you are not adding a locale that is not supported.

## Check if the desired locale is already supported by OPS portal

Steps:
1. Go to the [OPS Portal](http://OPS).
2. Sign into the portal with either your GitHub or VSTS credentials.
3. On the left navigation, search for the docset name you would like to add locales to.
4. Select the docset.
5. Click on the settings button and click on "Manage Localized Repos"
6. The supported locales are listed

## If the desired locale is not listed in OPS portal
This means you need to request the addition of a new locale. Please enter a request in [SiteHelp portal](http://aka.ms/sitehelp), as this can be done only by APEX Shanghai. Choose **trying to author/publish content for review.microsoft.com** option and include:

- **Date for when you want to start loc:**
- **Locales** - List the locales that you need support.

### Engineering Process to add new locales
* Add templates for new locales,This is a pre-requisite, all later steps have dependency on this being completed
    * create localize repos for templates, please contact [Duncan Mackenzie](mailto:Duncan.Mackenzie@microsoft.com)
    * Add new locales to [template localization configuration file](https://github.com/Microsoft/templates.docs.msft/blob/master/.localization-config) 
    * localize templates (IPM need to do this)
    * after templates are localized and handedback, please contact [Duncan Mackenzie](mailto:Duncan.Mackenzie@microsoft.com) to deploy the localized templates 
* Add new locales in language picker, please contact [Duncan Mackenzie](mailto:Duncan.Mackenzie@microsoft.com)
* Add new locale for legal page, please contact [Eman Shaheen](mailto:eshaheen@microsoft.com)
* Inform localization team for new locales need to be translated, make sure all localization tools support these locales. Inform [Sonja Saltzman](mailto:sonjas@microsoft.com).
* Add locale fallback logic for the newly added locales, please contact [Zhiliang Xu](mailto:Zhiliang.Xu@microsoft.com)
* Once the locales are added in OPS portal, user can create localized repos for content, provision OPS, and [request provisioning OL](Provision_Localized_Repo.md).
 
