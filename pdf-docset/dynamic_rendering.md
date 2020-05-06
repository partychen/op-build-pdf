# Dynamic Rendering
In order to decouple **content build** and **content rendering**, we introduce dynamic rendering mechanism. It brings the benefit that in some cases of template changing, user doesn’t need to rebuild their content. The template changes will take effective while user revisit the url. Because hosting will get the changes of template from backend and apply to the content at rendering runtime.  
That’s said in dynamic rendering, content build and rendering are separated. Under this case content build only builds the part of html body and provides additional information of how to use template. While hosting will render the page by getting both information of content and template. However, who can provide the template information? That’s a new concept names [template build](#whats-template-build).

> [!IMPORTANT]
> Separate the **content build** and **content rendering** doesn’t mean content can be totaly separated with template repository. Because when building content we still need information from template repository.  
> That means the [CRR](../partnerdocs/cross_repository_reference.md) you configured in configuration file will still be used while building repository content. Although we don't have the validation mechanism to check whether the CRR's url that users specified is same with theme, it's users reponsibilities to keep them consistent.

## What’s difference in content build
At first, it must be declared that static and dynamic redering is transparent to OPS customers. They don’t need to take care of that and all the user experience should keep same. The purpose of using dynamic rendering is to reduce our system coupling and reduce content build times. Certainly, it will bring some differences to developers.
Under static building/rendering, built result is an entire html page which contains both content and embedded template content such as css, js and etc. Local build result (html page) can be directly opened in browser and user can see content with good style. In this case, the html page seen by customer is same with that stored in our backend.  
However, under dynamic building/rendering, Local build result is a json file instead of html. The json file contains some parts, such as page content, page metadata and template addition information.  It can’t be directly viewed in browser but need more rendering logic to combine that with template. Obviously, in this case, the html page presents to user is different with that stored in our backend. Hosting has some runtime logics to render the page and makes the html page look like same with static one.

## What’s template build
Template build a new concept under dynamic rendering. The purpose of building template is reducing the page render time when user visits a page. The build progress of template does some fixed progresses and generates results. After building, the results will be published to DHS.

## How to provision a template
Every template should be provisioned as a theme under a site before user uses that. OPS doesn’t provide the feature of provisioning a template to a theme on portal. So for now, if user wants to use his own template in dynamic rendering, please contact build team for help.  
The following information is required to provide for provisioning a theme.
- Theme Name: It's a unique name of template, which is similar with docset name in content repository.
- Theme Url: Template git repository url.

After the template is provisioned as a theme, every commit that pushes to the template repository will trigger a build and build results will published to DHS. User can see the template building/publishing result on OPS portal. Besides, user can manual trigger template build on the portal.

> [!NOTE]
> Docs official theme (Default theme)  
> - Theme Name: Docs.Theme
> - Url: https://github.com/Microsoft/templates.docs.msft or https://github.com/Microsoft/templates.docs.msft.{locale|}  
> - Currently all the dynamic docset under Docs site will use official theme by default.

> [!NOTE]
> Currently template build doesn't support PR validation.

## How to use theme
1. Can user specify the theme of content?  
   For now, Docs site only has a default theme and OPS didn't provide the feature that let users choose their own theme.  
   If user want to use a different theme, please contact OPS build team for help.
2. Is user still able to use different branches of template to build content?
   Yes, that still works. User can use the same way as declared in [CRR](../partnerdocs/cross_repository_reference.md#whats-the-data-structure) to specify the theme branch that to be used to build/render content.
