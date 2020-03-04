# Open Localization Content Trouble Shooting

1. Make OP's error message friendly for us (easily show which line has error)
	* Loc markdown's github url(with commit)
	* Content error line
2. Guideline for finding localized file's corresponding source file/handoff xliff file/skeleton file and handback xliff file
	* Need Loc md file path and commit id
	* In Corresponding .translation-state -> by file path and commit id -> find translation item
	* handbackFilePath handbackFileCommit -> handback xliff in handback repo
    * handoffFileCommit -> Find the snapshot of handoff repo. Example:  [https://github.com/OpenLocalizationOrg/olhandoff/tree/7265c4d3ec9f3ee8d67fe2102371ff6aa4a757a4](https://github.com/OpenLocalizationOrg/olhandoff/tree/7265c4d3ec9f3ee8d67fe2102371ff6aa4a757a4)
	* Using the file hash -> find source/handoff xliff/skeleton file in ol-xliffcache folder. Example:
        * [https://github.com/OpenLocalizationOrg/olhandoff/tree/7265c4d3ec9f3ee8d67fe2102371ff6aa4a757a4/ol-xliffcache/OpenLocalizationOrg/hyperV.es-es/master](https://github.com/OpenLocalizationOrg/olhandoff/tree/7265c4d3ec9f3ee8d67fe2102371ff6aa4a757a4/ol-xliffcache/OpenLocalizationOrg/hyperV.es-es/master)
        * [Source](https://github.com/OpenLocalizationOrg/olhandoff/blob/7265c4d3ec9f3ee8d67fe2102371ff6aa4a757a4/ol-xliffcache/OpenLocalizationOrg/hyperV.es-es/master/560c4cea9b6163ed27afbf5d0f0b43caa2c5879f.md)
        * [Xliff](https://github.com/OpenLocalizationOrg/olhandoff/blob/7265c4d3ec9f3ee8d67fe2102371ff6aa4a757a4/ol-xliffcache/OpenLocalizationOrg/hyperV.es-es/master/560c4cea9b6163ed27afbf5d0f0b43caa2c5879f.xlf)
        * [Skeleton](https://github.com/OpenLocalizationOrg/olhandoff/blob/7265c4d3ec9f3ee8d67fe2102371ff6aa4a757a4/ol-xliffcache/OpenLocalizationOrg/hyperV.es-es/master/560c4cea9b6163ed27afbf5d0f0b43caa2c5879f.xml)
3. Guideline for content trouble shooting for content in standalone tool Xliff<-->md transformer
	* Create loc md off-line -> Cannot reproduce -> rehandback xliff
	* Compare handoff xliff and handback xliff source format
	* Expose xliff 2.0 to xliff 1.2
