This short lab demonstrates how to collect event logs directly from your local machine and gather up-to-date hardware and software information about your device. 
<br>
Splunk provides multiple ways to ingest data, and while the previous lab focused on parsing local raw files using the **Upload** option, this lab uses the **Monitor** input to continuously collect and index important system logs in real time.

 - we start by going to **settings**, and then **Add Data**
 - then follow up by selecting **Monitor** 
 ![screenshot of Monitor](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2a.png?raw=true)
 <br>
 - to collect event logs from my PC i chose 'Local Event Logs' amongst other options of data to collect, and to the right of the screenshot i selected to collect events data from the Application, System and Security.
<br>
 ![screenshot of selected items](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2b.png?raw=true)
 The benefit is that collecting Application, System, and Security event logs gives Splunk complete visibility into application behavior, operating system activity, and security/audit events. This enables full monitoring, troubleshooting, correlation, and security detection for a Windows host.
-
