# Open Localization Configuration File and System Files in different places

## Description

Open localization enable a new feature that the configuration file and system files can be placed in different places.

Options:
File(s) | Name(s) |	Original place	| Candidate places	| Relative Path	| Configurable | Example
--------|---------|-----------------|-------------------|---------------|--------------|--------
Configuration file | .localization-config | Source Repo | Source Repo | `.localization-config // the root folder`	| false  |[https://github.com/OpenLocalizationOrg/wdg-cpub-test/blob/master/.localization-config](https://github.com/OpenLocalizationOrg/wdg-cpub-test/blob/master/.localization-config)
`N/A` | `N/A` | `N/A` | Handback Repo | `ol-config/<source-repo-owner>/<source-repo-name>/<source-repo-branch>/.localization-config` | false |	[https://github.com/OpenLocalizationTestOrg/olhandback/tree/master/ol-config/OpenLocalizationTest/oltest/master/.localization-config](https://github.com/OpenLocalizationTestOrg/olhandback/tree/master/ol-config/OpenLocalizationTest/oltest/master/.localization-config)
System files | .translation-state |	Target Repo | Target Repo	 | `<system-file-name> // the root folder`  |	True	 |[https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/](https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/)
System files | .filepath-state | Target Repo | Target Repo	 | `<system-file-name> // the root folder`  |	True	 |[https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/](https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/)
System files | .localization-handback-report.md | Target Repo  | Target Repo	 | `<system-file-name> // the root folder`  |	True	 |[https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/](https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/)
System files | .localization-handoff-report.md |	Target Repo	| Target Repo	 | `<system-file-name> // the root folder`  |	True	 |[https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/](https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/)
System files | .localization-archive-report.md |	Target Repo | Target Repo	 | `<system-file-name> // the root folder`  |	True	 |[https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/](https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/)
System files | .localization-report.md |	Target Repo | Target Repo	 | `<system-file-name> // the root folder`  |	True	 |[https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/](https://github.com/OpenLocalizationOrg/wdg-cpub-test.fr-fr/)
`N/A` | `N/A` | `N/A` | Handback Repo |	`ol-handback/<taget-repo-owner>/<target-repo-name>/<target-repo-branch>/<system-file-name>` |	True |	[https://github.com/OpenLocalizationTestOrg/olhandback/tree/master/ol-handback/OpenLocalizationTestOrg/oltest.pl-pl/master/olsysfiles](https://github.com/OpenLocalizationTestOrg/olhandback/tree/master/ol-handback/OpenLocalizationTestOrg/oltest.pl-pl/master/olsysfiles)

## Usage
1. Configuration File:
    * You can put the configuration file in source repo or handback repo, the system will auto detect the place of the configuration file.
	* If the configuration file was put in one more places, ol system will merge these configuration files: sourcerepo-> handbackrepo-> passedfromAPI. The latter has higher priority.
		
2. System files:
    * You can chose to put the system files in target repo or handback repo, just change value of the "translationSysFileDestination" filed to "HandbackRepo" or "TargetRepo"
	* The default behavior is putting the system files in target repo
