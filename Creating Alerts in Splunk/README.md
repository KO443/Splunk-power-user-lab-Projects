<p align="center"> ALERTS

Alerts are searches based to run on a schedule or in real time. Alerts are helpful to alert a user or an analyst on when an event happens in your environment that may warrant immediate actions or further investigation.
<br>
<br>
In this Lab,I will dive into creating an alert by first writing my SPL search query


![screenshot of internallogindex](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8a.png?raw=true)


{index=_internal (log_level=ERROR OR log_level=WARN OR severity="high")} **This SPL Searches internal Splunk logs for any warnings, errors, or high-severity events.**
{ eval alert_time=strftime(_time, "%Y-%m-%d %H:%M:%S") } **This SPL Converts _time to a readable timestamp for the alert, y stands for year,m stands for month,d is dat, H is hour and so on.**
{stats count by log_level, component, alert_time, host } **this groups and counts events by level, component, host, and time**.
{where count > 0} **Only shows results when there are events so the alert won’t fire on empty searches).** 


I saved this as an alert by clicking **Save As** in the top-right corner right under **Search & Reporting** , then selecting **Alert**. This opens the alert configuration panel where you can define the criteria for the alert.

![sc of Alert panel](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8b.png?raw=true)
From here, I set the search to run on a cron schedule which is a method Splunk uses to automatically run alerts, reports, and other knowledge objects at specified intervals. Since I’m still learning cron syntax, I used **crontab.guru** to help generate the correct cron expressions.

In Splunk Alerts, you can configure trigger conditions to define what happens when the Alert fires such as **sending an email, creating a log entry, running a script, or performing other actions**. In my configuration, I set the alert to trigger for each result. 

Splunk’s **throttle** feature, which functions much like a “**snooze**” option, is useful when an alert may fire repeatedly throughout the day but isn’t critical or doesn’t require immediate action. Throttling prevents duplicate notifications within a specified time window, reducing noise while still keeping you informed.


Alert is Saved
![Sc of my alert](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8c.png?raw=true)

  
**************************************************************
<p align="center"> MONITORING MY OWN LOCAL WINDOWS NETWORK AND CREATING AN ALERT  

**************************************************************


*In this lab, i saved this as a REPORT because my enterprise license had expired and Splunk's free license does not let the user create an Alert*


I had previously done a similar Lab like this where i monitored my **'Local windows host onioting'**. in this repository but this time i monitored my **Local Windows Network**. 

to start this, go to **Settings, Add Data, Monitor, Local windows Network Monitoring**

![sc of select source](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8d.png?raw=true)

I gave my Network monitor a name then i chose all the components i would like to get data about like ipv6,ipv4,TCP,UDP etc as shown in screenshot above.

Hostfield was populated which is my computer/device name. I used the same index i used while monitoring my local host which is **my_computer_logs**
![sc of input settings](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8e.png?raw=true)

here is a review of my data
![sc of my data review](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8f.png?raw=true)

I saved the Local windows network monitoring data and this serach string auto populated on my search query
![](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8g.png?raw=true)

from the Index i created for monitoring my local windows network, i enetred a search query for an Alert that will alert me when unusual hiugh outbound traffic is leaving my local network.
![sc of report query](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8gi.png?raw=true)

![sc of search query](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/8gii.png?raw=true)
This alert monitors the total outbound network traffic from your computer and triggers whenever the amount of data sent exceeds 50 MB (50000000 bytes). It sums all outbound bytes over the search period and shows a result only if the traffic is unusually high. The alert helps detect potential issues like malware sending data out, unexpected large uploads, or misbehaving applications. Essentially, it acts as a warning when your computer is sending more data than normal, so you can investigate further.

