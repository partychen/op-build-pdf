# Open Localization Workflow Trouble Shooting

## Open Localization Live Site Owner Daily Work

1. Check the status of open localization system
    * All status can be found at https://capsinsight.azurewebsites.net/charts/postchip.html. Error, warning and queue length, performance and so on.
	* Found the details of Errors and Warnings from CHIP Database or Query Portal:
	    * SQL Server: capstrace.cloudapp.net
		* User Name: capsuser
		* Password: All know:)
		* Database: TraceStaging
        * [Query Portal](http://capsinsight.azurewebsites.net/Charts/AsyncUserQuery.aspx)
	* Log issues in the [SiteHelp portal](http://aka.ms/sitehelp).
	* Add new alert(s) if need.
	
2. Check and response open localization alerts
	* Check the alert email and response the alert email
	* Response should contains the detail of error, the reason and the solution
	* Log issues in [SiteHelp portal](http://aka.ms/sitehelp).
	
3. [Check gate-checkin 2-hourly test report](https://vscci.cloudapp.net/view/Open%20Localization/)
		
