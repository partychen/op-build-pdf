# Open Localization FAQ

## Handoff/Handback Repo Structure

> **Q**: ko-kr (ol-handback/windows-apps.ko-kr/master) is missing – do you think it is missing because ko-kr files moved to
> https://github.com/Microsoft/WDG.handback/tree/master/ol-archive/Microsoft/windows-apps.ko-kr/master?  
> **A**: YES. When handback files are successfully processed, they will be moved to “ol-archive” folder.

> **Q**: Is this the expected behavior, when files have been handed back and .md files generated with success that there should NOT be any > ol-handback folder?  
> **A**: ‘ol-handback’ folder does not only contain handback xliff files, but also OL reports. So “ol-handback” will always exist.

> **Q**: Once the issue that caused xlf file to go to the ol-poison folder is fixed and fixed file handback, will the file in the ol-poison folder be removed?  
> **A**: Currently, the poison handback file will NOT be removed even after the issue has been fixed.  

> **Q**: A pattern that seem to be forming is: if a file has not been updated since the last HO, the force HO seem to create an xlf under /master.  
> **A**: Currently, priority filter is NOT supported for Force-HO. All handoff files created by Force-HO will be placed under master folder      

> **Q**: Is there a way to clean-up the HO repo, so duplicate or misplaced files are removed altogether?  
> **A**: One way to clean-up HO repo is to delete all existing handoff files under “ol-handoff” folder (please keep all other ol- folders).  

> **Q**: Once clean will xlfs just be automatically generated? Or do we need to execute another force HO to get the xlfs generated.  
> **A**: One way to clean-up HO repo is to delete all existing handoff files under “ol-handoff” folder (please keep all other ol- folders). All handoff files that are NOT archived will auto created and placed under right folder. NO need to trigger Force-HO

## OL Auto HB Non-localizable Change

> **Q**: FileA contains a link to another topicB. This link is changed now.  No localizable text is changed. Will the fileA be republished (without loc handoff/handback) automatically?  
> **A** : Yes.

> **Q**: FileA has a reference to ArtB. We don’t localize the art, so it falls back to english.  The source ArtB is updated (modified picture, same name).  Will the loc fileA be republished automatically?  
> **A**: No, no re-publishing happened. But if you reload the published loc page, the artB will also be changed.

> **Q**: Metadata ms.date is updated in FileA by writer; will loc fileA be republished with updated ms.date automatically?  
> **A**: "ms.date" is non-localized content, so Yes, the loc fileA will be automatically HB and republished.

## OL Reporting

> **Q**: localization-satus.xlsx/ handback-status – what triggers the creation/update of these two files? These two files are constantly being updated every time there is a change on the target repo?  
> **A**: localization-status.xslx will be updated whenever handoff or handback files was processed by OL. Handback-status.xslt is will be updated whenever handback files are processed.  
In other words. Handoff processing updates only localization-status.xlsx, while handback processing will update both localization-status.xlsx and handback-status.xlsx.  

## Publishing

> **Q**: fileA contains a link to another topicB. This link is changed now.  No localizable text is changed. Will the fileA be republished (without loc handoff/handback) automatically?  
> **A**: YES    

> **Q**: FileA has a reference to ArtB. We don’t localize the art, so it falls back to english.  The source ArtB is updated (modified picture, same name).  Will the loc fileA be republished automatically?  
> **A**: No, no re-publishing happened. But if you reload the published loc page, the artB will also be changed. 

> **Q**: Metadata ms.date is updated in FileA by writer; will loc fileA be republished with updated ms.date automatically?  
> **A**: ms.date is non-localized content, so Yes, the loc fileA will be automatically HB and republ

## MD2XLIFF 

> **Q**:"Alt Text" is extracted in Xliff as a localizable text

> **A**:This is by design.Alt Text will show up only when the image cannot show in page.The pop-up text is actually tile of the image link.So xliff localized alt text.
