In this very short Lab, i displayed how to use transaction commands and defined what each argument does.
<br>
<br>
Transaction commands can help the Splunker investigate events. Events are grouped into transactions based on the associated and related identified fields of interest, if there is a relationship between the fields, then a transaction command can help enumerate that relation. Some of the Argumets that can be set are **maxspan**, **maxpause**, **startswith** & **endswith**.


I will write an SPL search where i use all 3 arguments in a search string
![screenshort of 3 transaction arg](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/3a.png?raw=true)

In this search, I used index=security* to look across all security-related indexes for events containing the source IP field src. Using the transaction command, I grouped SSH-related events that begin with SSHD, but only when they occur within a total window of 3 minutes (maxspan) and no more than 3 seconds apart (maxpause). This allowed me to identify tightly related SSH activity from the same source IP.

![screenshort of 3 transaction arg with eval](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/3b.png?raw=true)
<br>
in the serach string above, i added the search:  eval duration = tostring(duration, "duration") // The eval command in Splunk is used to create or modify fields by applying an expression or function. In this case, eval is combined with the tostring function, which converts a numeric value into a readable string. When used with the "duration" option such as in | eval duration = tostring(duration, "duration") Splunk takes a number representing seconds and transforms it into a human-readable time format (HH:MM:SS). For example, if the field duration originally contains 3600, it becomes 01:00:00 after applying the command, making the field easier to interpret and use in reports or dashboards. **table** command in this search puts **src** which represent client IP and **duration** in a table

<br>

NOTE
<br>
<br>
When to Use startswith: Use startswith when you want a transaction to begin only when a specific event occurs. It defines the trigger that starts grouping related events into a single transaction.

When to Use endswith:
Use endswith when you want the transaction to stop at a specific event. It sets the condition that closes the transaction.

Using Both Together
Using startswith and endswith together creates clear boundaries for a transaction, ensuring it begins and ends only at the events you define.


Quick Tip:

startswith controls what begins a transaction.

endswith controls what ends a transaction.

Both together give you complete, clean event grouping

* * * * * * * * * *  *  *  *   *   *   *    *     *   *
TRANSFORMING COMMANDS
* * * * * * * * * *  *  *  *   *   *   *    *     *   *
Transforming commands in Splunk are search commands that take your raw events and reshape them into statistical tables, often grouped, aggregated, or summarized. They transform the data from event-by-event form into a report-style format. Eg: chart,top,rare, stats,shownull, fillnull

Key characteristics

 - They aggregate or group events.

 - They produce tables, not raw events.

 - They often require fields to be present (like stats, chart, etc.).

 - They are used for reporting, dashboards, and analytics.

 In the serach below,i searched for the word 'fail' hence i used fail with a wildcard which will search for failure, failed or just fail ("fail*") in the field values of security index. **top** is a transformning command that seraches for top 10 most common values by defult and counts and isplays the value in %, so adding limit=20 argument makes it provide 20 most common values and the showperc=false is an argument that dialbles the percent from displaying and displays answer in numbers
 

 
 ![screenshot of transform string](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/3c.png?raw=true)
 
**One key tip i learned in my splunk course is that single quote seraches field names while double quote searches field values** for eg: "fail" searches for fail in field values while 'fail' would have searched for fields titled **fail**
<br>
<br>
This search string below i used transforming commands stats & fillnull. I searched into my security index, stats is a transforming command, because it aggregates and reshapes the field (user) as "Login Name". The **Value** function will Collects all unique users per IP address (src) and displays them in a single row, **count** function will count the total number of occurences of user per Ip address (src) and **by** which is a boolean operator in this serach string will group results by src so each row represents a different source.

![screenshot of another transforming string](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/3e.png?raw=true)
![screenshot of another transforming stringresult](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/3d.png?raw=true)
