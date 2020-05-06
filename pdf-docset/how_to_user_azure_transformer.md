# How to transfer markdown with from Azure syntax to OPS syntax with Azure Transformer (shorten as AT)
Before you read this, you can read [Azure Transformer](azure_transformer.md) at first to know what the transformer will do.  
This article is a guide line of how to using the transformer to transform your content to OPS syntax. The total step can be separated to three parts, namely pre-migration, migration and post-migration.

# Pre-Migration Step
This step lets you prepare the environment to run migration. Including two main parts
- provision your repository in OPS system, so that you can do post-migration verification
- prepare locale environment to run AT

| Order | Decription | Sample command | Hint |
| ----- | ---------- | -------------- | ---- |
| 1 | Provision your repository to OPS system. |   | you can got to our [portal](https://ops.microsoft.com) to do provision. |
| 2 | Clone that repository to local. | git clone https://github.com/openpublish/azure-docs-pr |  |
| 3 | Create a new branch based to do migration. | git checkout -b master-migration | make sure you are at the branch you want to transform content before input the command. |
| 4 | Download the migration script to the repository root folder. |  | Migration powershell scritps [Download](https://opbuildstoragesandbox2.blob.core.windows.net/azure-migration/AzureMigration.ps1).  |

# Migration Step
This step is the content transform main step. You need to run the powershell you download in pre step.

| Order | Decription | Sample command | Hint |
| ----- | ---------- | -------------- | ---- |
| 1 | Run the migration script in the repository root folder. | powershell .\AzureMigration.ps1 | If you meet any permission issue to run powershell, please search the answer in https://google.com |
| 2 | See the migration report log.html in log folder and to do some fix if necessary. | | most are warnings that won't block the build/publish, you can leave them, if there's some errors, please fix them before you do the following steps. |
| 3 | Commit and check in the migrated content to the repository. | <ul><li>git add .</li><li>git commit -m "some commit message"</li><li>git push origin master-migration:master-migration</li></ul> | Push to a the new branch will also trigger a build and won't pollute the master branch. So it's convenient for you to do another round migration.|

# Post Migration Step
| Order | Decription | Sample command | Hint |
| ----- | ---------- | -------------- | ---- |
| 1 | After you push the content, the build will be triggered and you'll receive the build report later. | | You can logon to new [portal](https://ops.microsoft.com) to see the build status and history |
| 2 | See the build and publish report to check if there's some issue you need to fix with the content. | | |
| 3 | Click the link in the given in the email to check the publish page status. | | |
