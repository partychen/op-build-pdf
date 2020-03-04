# Localization file status
## Error messages

Status | Description
-------|------------
Non localizable -> Not to be localized | The file is never localized and will not localized unless the configure file change. (It includes some files that are not Markdown)
Handoff failed -> Handoff transform failed | Transform to xliff fail.
Ready for handoff | Latest xliff file is already generated, but the vendor does not download it to translate.
In Translation | The vendor is translating the latest xliff file. And the xliff file is put to cache folder.
Handback failed -> Handback transform failed | The latest xliff file has been translated and uploaded, but transformed back to markdown failed.
Handed back: in sync with en-us | Successfully transformed back to markdown. And the localized file is in the same version of EN-US version.


Handbacked: not in sync with en-us-> Handed back: not in sync with en-US.

Successfully transformed back to markdown. But a force handoff or rename happen, or translationtype/priority changed, a new xliff is generated.
