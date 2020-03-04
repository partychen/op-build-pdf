
Teams might decide to go live for the first time in two stages: 

1. Soft launch (GOTO Live flag = OFF)
2. Live/public launch (GOTO Live flag = ON)

> [!IMPORTANT]
> GOTO Live flag is off by default when a docset is created. 

> GOTO Live flag is enabled for all locales at the docset level. So any content that is on the live branch for localization docsets will also go live at the same time.

## Soft launch (GOTO Live flag = OFF) 
Merge your master branch to `live` branch. 

If GOTO live flag is off for a docset, the docset will be published to live branch. The content is actually published, but hidden at http://docs.microsft.com or any other PROD end point. Instead it's available at https://review.docs.microsoft.com with the same URL structure BUT on live branch. So the testing can be running on the review.docs.microsoft.com.

This is useful for teams to test their merge from master to live branch and have the content published by hidden to the public. Once the team is ready to go live, there is no need to republish.

> [!NOTE]
> You cannot do soft launch for localization once the GOTO Live flag has been enabled for English.

## Public launch (GOTO Live flag = ON)
This is when your content becomes available to the public. 

> [!IMPORTANT]
> Going live for the `first time ONLY for a docset` is controlled via a "GOTO Live" flag that only your APEX onboarding PM can enable, to make sure everything looks correct. Thus, you need to make sure you have an onboarding PM and a tick tock plan well before reaching this point. See [onboarding steps](../onboarding-steps.md) for more information.       

Once the flag is on, the content in the live branch in docset is available to public, say https://docs.microsoft.com. If the content is already published via a soft launch, OPS doesn’t do any re-publish, just bring out the hidden contents that are published in soft launch.