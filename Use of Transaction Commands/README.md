In this very short Lab, i displayed how to use transaction commands and defined what each argument does.
<br>
<br>
Transaction commands can help the Splunker investigate events. Events are grouped into transactions based on the associated and related identified fields of interest, if there is a relationship between the fields, then a transaction command can help enumerate that relation. Some of the Argumets that can be set are **maxspan**, **maxpause**, **startswith** & **endswith**.


I will write an SPL search where i use all 3 arguments in a search string
![screenshort of 3 transaction arg](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/3a.png?raw=true)

In this search, I used index=security* to look across all security-related indexes for events containing the source IP field src. Using the transaction command, I grouped SSH-related events that begin with SSHD, but only when they occur within a total window of 3 minutes (maxspan) and no more than 3 seconds apart (maxpause). This allowed me to identify tightly related SSH activity from the same source IP.

![screenshort of 3 transaction arg with eval](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/3b.png?raw=true)
<br>
in the serach string above, i added the search:  eval duration = tostring(duration, "duration") // The eval command in Splunk is used to create or modify fields by applying an expression or function. In this case, eval is combined with the tostring function, which converts a numeric value into a readable string. When used with the "duration" option such as in | eval duration = tostring(duration, "duration") Splunk takes a number representing seconds and transforms it into a human-readable time format (HH:MM:SS). For example, if the field duration originally contains 3600, it becomes 01:00:00 after applying the command, making the field easier to interpret and use in reports or dashboards.
<br>
*   *   *    *     *   *

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
