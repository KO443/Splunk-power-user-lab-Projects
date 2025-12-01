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


