# Open Localization Trouble Shooting

## API Trouble Shooting
* [Open Localization API Trouble Shooting](OL_API_TroubleShooting.md)
* Open Localization has some API can be called to start handoff/handback/archive workflow and get corresponding result. API trouble shooting is mainly used to analyze the ***error return by APIs*** and resolve the errors.

## Workflow Trouble Shooting
* [Open Localization Workflow Trouble Shooting](OL_Workflow_Troubleshooting.md)
* Open Localization Backend will do the long-time-running handoff/handback/archive according to the requirement. During the long-time-running process there will be errors, warning traced and the whole workflow maybe fail caused by the environment(local git) issues or bugs. Workflow trouble shooting is mainly used to maintain the whole workflow process and keep the ***localization state*** correctly.

## Content Trouble Shooting
* [Open Localization Content Trouble Shooting](OL_Content_Troubleshooting.md)
* Open Localization Transformer will translate the markdown/yaml files to xliff files and translate the localized xliff files to markdown/yaml files. During this process there will be content error caused by ***transformer*** and break the ***publishing*** process. Content trouble shooting is mainly used to  analyze the content issue, find corresponding xliff/skl/md files.
