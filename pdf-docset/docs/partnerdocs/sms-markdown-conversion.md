# Converting SMS content to markdown

## Prerequisites: 

Install pandoc on your machine http://pandoc.org/installing.html

## Steps:

1.	Log into SMS and switch to batch mode
2.	Select each of the articles in your target dev center using the left navigation pane
3.	Click “Export” and save the resulting CSV to a file. 
4.	Open PowerShell ISE and paste the following script into the script editor. This will output HTML files to a new directory called MSDN. 

  ```powershell
  function getHTMLFromSmsExport($file) {
      cd $PSScriptRoot
      $export = (import-csv $file)

      new-item -ItemType Directory -Force -Path MSDN

      foreach ($row in $export) {
          $url = "https://msdn.microsoft.com/en-US/library/" + $row.ContentId
          echo $url

          $out = "MSDN\"+$row.ContentId+ "-" + $row.ContentName+".html"

          $httpContent = Invoke-WebRequest -URI $url -TimeoutSec 15
          $htmlContent = $httpContent.ParsedHtml.getElementById("content")
          if ($htmlContent -ne $null) {
              $html = $htmlContent.OuterHTML
              $html | Out-File -FilePath $out -Encoding utf8

              $images = $httpContent.ParsedHtml.getElementById("content").getElementsByTagName("img")

              foreach ($image in $images) {
                  $chunks = $image.src.Split("/")
                  $outName = "MSDN\" + $chunks[$chunks.Length -1]

                  Invoke-WebRequest -URI $image.src -OutFile $outName -TimeoutSec 15
              }
          }
      }
  } 
  getHTMLFromSmsExport("smsexport.csv") #Update this to point to your export CSV 
  ```
5.	Next, you can convert the html content (which is just the page content without any chrome) to Markdown, also using PowerShell

    ```powershell
    cd MSDN
    $files = dir

    foreach ($file in $files) {
        if ($file.Extension -eq ".html") {
            $out = $PSScriptRoot + "markdown\" + $file.BaseName + ".md"
            echo "pandoc $file -f html -t markdown -o $out"
            pandoc $file -f html -t markdown-raw_html-native_divs-native_spans+startnum-link_attributes-header_attributes+hard_line_breaks --atx-headers -o $out
        }
    }
    ```
  
  6. Now that your content is converted into markdown, it can be added to your git repository.
