<p align="center">Home Dashboard

********************************
A home dashboard is the dashboard displayed on the Splunk home screen each time you log in. You can set your user preferences to open this dashboard instead of Search & Reporting, allowing you to see it automatically at login.

1. I will dive into creating a home dahsboard by writing my search query
![Homedash serach query](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99b.png?raw=true)
The SPL looks inside Splunk’s own logs, pulls out events that have a log level and a reason, formats the timestamp into a readable date, removes duplicate reasons, and lists each unique reason with its log level and date sorted by date.<br><br>This SPL search begins by scanning the _internal index for events that contain a log_level field (index=_internal log_level=*), then uses eval with strftime to turn _time into a readable Date (| eval Date=strftime(_time, "%m/%d/%Y")). 
It next applies a where filter to keep only events where reason exists (| where isnotnull(reason)), and formats the output into a table showing only log_level, reason, and Date (| table log_level, reason, Date). After that, it removes duplicate reasons using dedup (| dedup reason), and finishes by sorting all remaining events by Date (| sort Date).


2. After writing my search, I saved it by clicking Save As and selecting New Dashboard, which opened the dashboard configuration page. I then entered the dashboard title, description, and permissions, selected Classic Dashboard as the dashboard type, and entered the panel title as shown in the screenshot
![Dashboard config](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99c.png?raw=true)















































***********
Drilldowns

Drilldowns add interactive functionality to dashboard panels. For example, clicking a value in a chart or table can take you to a related search, open another dashboard, or display a corresponding report.

Tokens

Tokens allow dashboards to accept user input—such as dropdown selections, text fields, or time ranges—and use that input dynamically in searches, panels, and drilldowns.

Reports

Reports are essentially saved searches. They can highlight important events, display statistics or tables, and generate visualizations. Reports can also be scheduled or used as the basis for alerts and dashboards.
