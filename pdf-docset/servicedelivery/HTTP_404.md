# [ALERT ACTIVATED] - Http 404 GreaterThan 1000 (Count) in the last 5 minutes

Follow this  TSG  when you get HTTP_404 error
------------------------------------------------

Open Sql Server Mannagement Studio and Follow below steps

  Step1.Connect to SQLServer capstrace.cloudapp.net via SSMS with capuser
  
  Step2.Make sure the connected database is TraceStaging. Copy and paste the below query to SSMS and replace <start time>and<end time >        with the time in the alert email. Note that the time in both alert email and the SQL query are in UTC. Example: 2016/05/07             19:54:00
```
SELECT * FROM [APITraceLogs] with (nolock)
WHERE Environment='prod'
AND ComponentName ='Microsoft.Document.Hosting.WebApi'
AND LogEventTime between '<start time>' and '<end time>'
AND ResultCode = 404

```
    
  Step3.Run the query in SSMS. More than 1000 rows should be returned as per alert...
  
  Step4.Expand ApiInput column in the result set.
  ![APiIntput](images/http_404.png)
  Step5.If the Patteren is VS.Vsdownload this is a known issue,Kindly update SE and no more action needed.  
  
   

  
