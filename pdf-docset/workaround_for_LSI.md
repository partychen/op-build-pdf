# Service rollback options for new deployment bits
Due to the high rate of LSI happening after each deployments, operation team wants to know if there's a way that can quickly work around the issue due to this time's deployment. So they can unblock partner immediately and leave the investigation to OPS team later.

# Options of rollback
## Rollback by using last version of build tool
OPS provide a mechanism that using different version of build tool to build content. Every deployment will generate a new version of build tool. Sometimes the latest version of build tool may have bug so we can try to use older one to unblock partners.  
The following steps is letting you to check whether this rollback way can work.
1. Create a new branch on the failed repository. If you don't have permission, you can fork the repository to your own and provision that, then you can do the next step.
2. Set [**package_version**](../partnerdocs/publish-configuration.md) in publish configuration file with specified version number.
3. Check build results, if it is OK and can unblock partners, merge it to the corresponding failed branch.

> [!NOTE]
> Build team will add the build tool version information in deployment notification in the future.

> [!TIP]
> You can use the following command line with [nuget.exe](https://opbuildstorageprod.blob.core.windows.net/opps1container/Tools/Nuget/nuget.exe) to list all package versions that can be used.  
> `nuget.exe list opbuild.scripts -Source "https://www.myget.org/F/op/api/v2" -AllVersions -NonInteractive`  
> The version is ordered by string but not by integer. Please remember that 1.20.1 is newer than 1.7.0.

## Rollback by turning off some feature flags 
While adding some new feature with risk, OPS may add some feature flags to controller that. Sometimes the flags are on repositories while sometimes they are global configured.  
If you find the error is obviously related to new feature, you can try to turn that feature flags off either on modifying publish configuration file or change the [global configuration](https://capservice.visualstudio.com/CAPS/_git/Configuration?path=%2Fopenpublishingbuild%2Fop-build-prod.json&version=GBmaster&_a=contents)

> [!IMPORTANT]
> Change the global configuration will result in all the worker role restart. The messages that are already in processing will be picked up and processed again after that.
