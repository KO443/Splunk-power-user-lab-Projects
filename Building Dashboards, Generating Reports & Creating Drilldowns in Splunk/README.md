<p align="center">Home Dashboard

********************************
A home dashboard is the dashboard displayed on the Splunk home screen each time you log in. You can set your user preferences to open this dashboard instead of Search & Reporting, allowing you to see it automatically at login.

1. I will dive into creating a home dahsboard by writing my search query
![Homedash serach query](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99b.png?raw=true)
The SPL looks inside Splunk’s own logs, pulls out events that have a log level and a reason, formats the timestamp into a readable date, removes duplicate reasons, and lists each unique reason with its log level and date sorted by date.<br><br>This SPL search begins by scanning the _internal index for events that contain a log_level field (index=_internal log_level=*), then uses eval with strftime to turn _time into a readable Date (| eval Date=strftime(_time, "%m/%d/%Y")). 
It next applies a where filter to keep only events where reason exists (| where isnotnull(reason)), and formats the output into a table showing only log_level, reason, and Date (| table log_level, reason, Date). After that, it removes duplicate reasons using dedup (| dedup reason), and finishes by sorting all remaining events by Date (| sort Date).


2. After writing my search, I saved it by clicking Save As and selecting New Dashboard, which opened the dashboard configuration page. I then entered the dashboard title, description, and permissions, selected Classic Dashboard as the dashboard type, and entered the panel title as shown in the screenshot
![Dashboard config](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99c.png?raw=true)

The Home Dashboard is initially set to a light theme. To switch to dark mode, click the Edit button at the top right and toggle between the light and dark themes based on your preference. Open link in a new tab to see the LOg_level, Reason and Dates all displayed on my dashboard.
![homedash set up](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99d.png?raw=true)

To make he newly set up dashboard a Home Dashboard, click on the 3 dot at top right corner 
![make homedash](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99dc.png?raw=true)


*****************************************************
 <p align="center"> Creating Tokens off dashboard

****************************************************
Tokens allow dashboards to accept user input—such as dropdown selections, text fields, or time ranges—and use that input dynamically in searches, panels, and drilldowns.

I will be continuing from the previous section where i created my Home Dashboard, to create Token off the Dashboard, I first start by
1. going to edit in the Dashboard then Add input. From the Many options in the input dropdown, i chose text and then clicked submit, I added text, submit 
 

![sc of add inpout token](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99e.png?raw=true)

2. hdhdhd
3. jsdjsdjsj
4. ldld















































***********
Drilldowns

Drilldowns add interactive functionality to dashboard panels. For example, clicking a value in a chart or table can take you to a related search, open another dashboard, or display a corresponding report.


Reports

Reports are essentially saved searches. They can highlight important events, display statistics or tables, and generate visualizations. Reports can also be scheduled or used as the basis for alerts and dashboards.
