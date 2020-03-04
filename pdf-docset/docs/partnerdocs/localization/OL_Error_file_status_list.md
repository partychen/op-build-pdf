# Handback Validation

Error Code | Description | Error Message 
------|-------------| --------------
out-of-handoff-scope | Handback file is rejected as its source file is out of latest handoff scope | "file {fileName} is out of handoff scope"
old-handback-version | Handback file is rejected as higher version has already been checked in | $"Targeting source file commit {SourceFileCommit} is lower than latest handed back source file commit {latestHandedBackSourceFileCommit}"
handback-file-name-mismatch | Handback file name: {handbackFileName} is different with handoff file name: {handoffFileName}
handback-translation-type-mismatch | The handback translation type in file path {handbackFilePath} is not match with handoff type {handoffType}"
transformer-updated | Handback file is rejected as new version of handoff xliff is created due to transformer update. 
invalid-yaml-header | Format of yaml header block in converted loc MD file is invalid

# All Open Localization error & file status list

* [The list of the file statuses](https://mseng.visualstudio.com/VSChina/_git/OpenLocalization?path=%2Fsrc%2FOpenLocalization.Common%2FModels%2FSourceFileState.cs&version=GBmaster&_a=contents)
 
* [The list of the errors](https://mseng.visualstudio.com/VSChina/_git/OpenLocalization?path=%2Fsrc%2FOpenLocalization.Common%2FErrorHandling%2FErrorDefinitions.xml&version=GBmaster&_a=contents)
