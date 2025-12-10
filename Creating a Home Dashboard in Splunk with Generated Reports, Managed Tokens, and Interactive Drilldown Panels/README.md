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
Tokens allow dashboards to accept user input such as dropdown selections, text fields, or time ranges and use that input dynamically in searches, panels, and drilldowns.

I will be continuing from the previous section where i created my Home Dashboard, to create Token off the Dashboard, I first start by
1. going to edit in the Dashboard then Add input. From the Many options in the input dropdown, i added **text** and **submit**, as inputs so when the user enters a text in the field they can also use the subit button.
![sc of add inpout token](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99e.png?raw=true)

2. I labeled the new input as **loglevel** which also is assigning it a token value of loglevel , enabled **Search on Change** by checking the small box, and named the token **loglevel** before clicking Apply at the bottom right. Enabling Search on Change means that any time the user selects a different value from this input, the dashboard automatically reruns all dependent searches using the updated token value, no refresh button needed. This makes the dashboard more dynamic and responsive, updating panels instantly based on the user’s selection.

![sc of token input config](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99f.png?raw=true)

3. To Edit search, and add our new token `$loglevel$` ($ is used to indicate token in splunk), we will click on the magnifying glass icon as shown in the screenshot. Edit the search string and replace the log_level=* with `$loglevel$`
 and the hit **Apply**. This allows the **search** and the dashboard panels to update dynamically based on whatever log level the user chooses.
 
![token search edit](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99g.png?raw=true)

![add token tosearch](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99h.png?raw=true)


4. I typed INFO into the text input (since the log_level field originally contained values like INFO and WARN) and clicked **Submit**. This passes the value through the loglevel token and applies it to the log_level field in the search, returning results that match the selected log level.

![sc od txtinput n submit](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99i.png?raw=true)

![sc of txtinput n submit](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99j.png?raw=true)

6. I created another input for **time** in the dashboard and configured it according to my requirements. I labeled the input **time**, assigned the token name **time**, and left the time range set to its default value of the last 7 days.
![input of time](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99k.png?raw=true)


7. The dashboard text, submit and time input looks like this.
![Home Dashboard input](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99l.png?raw=true)

8. I went to **edit**, then selected **Edit Search** by clicking the magnifying glass icon in the dashboard. From there, I changed the time range setting from Use time picker to Shared time picker, and clicked **Apply** to save the new preference. This change allows the search to use the dashboard’s shared time input, meaning the time range selected by the user is automatically applied to all panels that reference this shared time token, keeping the entire dashboard synchronized and consistent. With this new change it is searching for 1 month rather than the default last 7 days search. So Dashboard title can now be **'Error/INFO/Warn messages seen in the past month'**

![edit search shared timepicker](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99m.png?raw=true)

**********************************************
<p align="center"> Adding Reports to the Home dashboard with Maganed Tokens interactive drilldown Panels

**********************************************

Drilldowns add interactive functionality to dashboard panels. For example, clicking a value in a chart or table can take you to a related search, open another dashboard, or display a corresponding report.<br> <br>
Reports are essentially saved searches. They can highlight important events, display statistics or tables, and generate visualizations. Reports can also be scheduled or used as the basis for alerts and dashboards.

1. For this section of the Lab, i will start by searching my SPL query. This searches across all indexes (index=*) for events that contain “.exe” anywhere in the raw event data. It also filters the results to only include events from the specific host **mybox** which is the host for my device. Then uses the **table** command to neatly display only the relevant fields Name, Path, and Commandline so we  can clearly see which executable ran, where it was located, and the exact command used to execute it.


I saved this search as a report and added it to the existing Home dashboard I created in the previous section, titled ‘Error/INFO/Warn messages seen in the past month’. 

![search string report](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99n.png?raw=true)

2. This is the result of the serach. It perfectly tables the .exe files, their path and Commandline. I then edited the report’s schedule so it runs automatically every Monday morning at 6 AM, ensuring the dashboard always reflects the most up-to-date results.
![edit report sched](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99o.png?raw=true)

The Report is Titled **SOC_Report_Executableseen**, and this is the configuration page after clicking **Edit schedule**. 

![report cron sched](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99p.png?raw=true)


3. To make my existing dashboard an executable dashboard, i went to my home dashboard: 'Error/INFO/Warn messages seen in the past month', clicked on 3 dot option left sideafter edit dashboard, clicked edit drilldown and chose ** link to search** (this will make the dashboard clickable).

To make my existing dashboard an executable dashboard, I opened my Home dashboard ‘**Error/INFO/Warn messages seen in the past month**’, clicked the three-dot menu next to Edit Dashboard, selected **Edit Drilldown**, and chose **Link to Search**. This enables drilldown functionality, allowing users to click on dashboard panels and be taken directly to Search.

<img width="672" height="402" alt="image" src="https://github.com/user-attachments/assets/0f65cd89-197e-45bb-834c-b944a356432b" />


4.  Here is what the dashboard looks like ater it is clickable. Clicking on any of the link will add to search.

<img width="780" height="423" alt="image" src="https://github.com/user-attachments/assets/3ac4b856-627d-4472-8ad5-b6bde747174f" />

5. while in the **drilldown editor**, i explored another option in the configuration to manage tokens on this dahsboard on click.

![drilldown editor](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99s.png?raw=true)

- I set the token name **userclick** with the preset token value **click.value2$** so that whatever is clicked be it any value or any cell clicked in this **table chart** will be generated in events. 

- To make the new token **userclick** functional, I added a new panel to the Home dashboard. I clicked **Add Panel** at the top of the dashboard, selected **Events**, and set the panel title to** User's Input**. In the search for the panel, I referenced the token by using: index=* $userclick$. Finally, I adjusted the time range to **All Time** so the panel can return results whenever a user triggers the token through a drilldown action.

![Add panel config](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/99t.png?raw=true)





