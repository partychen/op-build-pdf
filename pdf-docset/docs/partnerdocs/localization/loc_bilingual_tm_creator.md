# Biligual TM creator

[Zip File location](https://microsoft.sharepoint.com/teams/Visual_Studio_China/MSDN/Shared%20Documents/Open%20Localization/Tools/BilingualCreator.zip)

1. Prepare DDUE translated xliff
    * If you're creating bilingual files based on TTX files or DDUE translated xliff not from CAPS, pls skip this step and go to step 2.
    * If you already have DDUE translated xliff files ready, pls skip this step and go to step 3.
    * If you're creating bilingual files based on DDUE translated xliff from CAPS, pls do this step.
        1. Copy handback package zip files from \\capsdrop\CAPS\Archive\Handback to your local.
		2. Unzip handback package zip files copied in previous step.
		3. There will be multiple xliffs files at different blob revision and/or metadata revision for one article GUID.
		4. Use this tool to pick up xliff files which blobrevision/metadatarevision=latest en-us checkin/metadata revision. Open cmd, go to path where the tool is in, run below command with arguments:

		    `BilingualCreator.exe mergedduexliff dduexliff:<folder full path of ddue upzipped xliffs, subfolders organized by locale> outputfolder:<output folder>`
2. Create bilingual files
    * Make sure you have DDUE translated xliff or TTX files ready.
	* Make sure you have MD untranslated xliff ready.
	c. Run below command to generate bilingual files. Open cmd, go to path where the tool is in, run below command with arguments:
	    * If translated file is ttx file, run 

          ` BilingualCreator.exe createtm sourcetype:ttx dduexliff:<folder of ttx files, must including en-US folder> mdxliff:<md xliff folder, subfolders organized by locale>  xliffversion:<version of bilingual xliffs, could be: v12, v20, representing for xliff 1.2 and xliff 2.0>  outputfolder:<output folder>`
		 
         sample

			`BilingualCreator.exe createtm sourcetype:ttx dduexliff:E:\project\ttxtm\AcomDoc\ttx mdxliff:E:\project\ttxtm\AcomDoc\mdxliff outputfolder:E:\project\ttxtm\AcomDoc\bilingual`
        
        * If translated file is DDUE translated xliff file, run

		    `BilingualCreator.exe createtm sourcetype:xliff dduexliff:<folder of DDUE translated xliff files, subfolder organized by locale> mdxliff:<md xliff folder, subfolders organized by locale>  xliffversion:<version of bilingual xliffs, could be: v12, v20, representing for xliff 1.2 and xliff 2.0>  outputfolder:<output folder>`
			
			sample

			`.\BilingualCreator.exe createtm sourcetype:xliff dduexliff:E:\project\md_tm_creation\MABizTalk\mergeddduexliff mdxliff:E:\project\md_tm_creation\MABizTalk\mdxliff2\ho_2016_05_19  outputfolder:E:\project\md_tm_creation\MABizTalk\bilingual`
			
