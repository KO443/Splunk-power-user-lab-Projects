This short lab demonstrates how to collect event logs directly from your local machine and gather up-to-date hardware and software information about your device. 
<br>
Splunk provides multiple ways to ingest data, and while the previous lab focused on parsing local raw files using the **Upload** option, this lab uses the **Monitor** input to continuously collect and index important system logs in real time.

 - we start by going to **settings**, and then **Add Data**.
 - then follow up by selecting **Monitor**
 ![screenshot of Monitor](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2a.png?raw=true)
 - to collect event logs from my PC i chose 'Local Event Logs' amongst other options of data to collect, and to the right of the screenshot i selected to collect events data from the Application, System and Security then i clicked **next** to 'input setting'.
![screenshot of selected items ](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2b.png?raw=true)
The benefit is that collecting Application, System, and Security event logs gives Splunk complete visibility into application behavior, operating system activity, and security/audit events. This enables full monitoring, troubleshooting, correlation, and security detection for a Windows host.
 -  i left my index at default and host field value which is the title for the input which i called as "mybox".  
 ![screenshot of host field value ](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2c.png?raw=true)
 - after clciking next it took me to the review of the set up of 'Local Events logs' and then i clicked **submit**. Index shows as SSA which is system security and application.
 ![screenshot of review](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2d.png?raw=true)
<br>
<br>
Up next, I will set up **local Windows host monitoring** to capture hardware and software events. This helps provide deeper visibility into system activity and supports both troubleshooting and security analysis.
<br>
  
 -   I started this by going to Settings, Add Data and Monitor.
 -   select **Local Windows host monitoring** ![screenshot of LWHM ](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2e.png?raw=true)
 -  After selecting Local Windows Host Monitoring, I entered the collection name as my_local_logs and selected the event types to log all the available options which were: Computer, Operating System, Processor, Disk, Network Adapter, Service, Processes, Driver, and Roles. I chose a 30-second interval, which allows the system to collect timely updates without overloading the host, providing near–real-time visibility into hardware and software activity. ![screenshot of collection name ](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2f.png?raw=true)
 -  I set the Host field value to "mybox" and and left the Index as the default. Here is the final review before clicking Submit. ![screenshot of review](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2g.png?raw=true)  ![screenshot of submit](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2h.png?raw=true)
 
 -  I verified that the data was being indexed correctly by running a search against my newly created Windows host monitoring input. ![screenshot of search](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/2i.png?raw=true)
<br>
<br>
This SPL search confirms that my Windows host monitoring data is successfully ingesting into Splunk. By filtering on source="my_local_logs", host="mybox", index="my_computer_logs", and sourcetype="WinHostMon", the search returns only the hardware and software inventory events collected from my local machine. These events include details about drivers, operating system components, disk and processor information, network adapters, roles, services, and other system-level metrics. The results verify that the monitoring input is configured correctly, the data is landing in the intended index, and the host and sourcetype are being properly assigned, confirming that Splunk is collecting timely system updates based on the 30-second interval I configured.
 
 
