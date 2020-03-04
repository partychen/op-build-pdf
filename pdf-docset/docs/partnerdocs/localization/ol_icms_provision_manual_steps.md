#Manual creating repos before provision repo via ICMS portal

## Description
As OSS team remove the "creating repo" permission of our service account for Microsoft github org, right now both OL and OP can 
NOT automatically create public/private repo under Microsoft/Azure/Pouwershell orgs during provision step, this requires that users need firstly use the Microsoft Open Source Portal to create the repos themself and then provision them via ICMS

## NOTICE

1. All repos under Microsoft/Azure/Powershell want to be provisioned in ICMS need do these manual step before the provision.  
2. After we move to MicrosoftDoc org, these manual steps will be no more needed. Sandre is working on the MicrosoftDoc org now.

## Steps

1. Create repos in your organization or in Microsoft docs org using Microsoft Open Source Portal, please reference to [How To Create Repo Using Microsoft Open Source Portal](loc_create_repo_using_open_source_portal.md) for the details.  
    a. Create Loc repos, each language should be mapping to one repo.   
    b. Make sure add the correct **Admin Team** during the creation step, you need be in this **Admin Team** to make sure you can go further.      
    c. Add '**olprod**' account to the loc repos as the **admin**. You can also direcly add 'olprod' account to your **Admin Team**.    
    d. Make sure the loc repo name is match with the **ICMS name format**.   
  
2. Use ICMS portal to provision the repo after you creating the loc repos.
