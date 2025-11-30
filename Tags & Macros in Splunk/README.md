          
<p align="center"> TAGS IN SPLUNK    

*   *   *    *   *   *                                               
A tag in events can act as quick reminders. They can be uses to corelate field value pairs. Tags make data more undertstandable and they are case sensitive when searching. In his short Lab i will be showcasing how to create a tag.

*please click on image and open link in a new tab to see it clearer so you can zoom in if needed.*


 1. In splunk, i started by giving a tag to a certain eventcode so that whenever it appears in my search result, i can be able to figure out what it is.
 in this SPL search i loooked into all indexes for eventcode=4624, and under **Actions**, i clicked on the dropdown arrow in the same row as event code 4624
 ![screenshot of eventcode](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/6a.png?raw=true)

 
 2. After clicking on the actions button for eventcode 4624, i added login as the tag. which is what event code 4624 stands for, this tag will always remind me what i am looking at whenever i see the evenyt code in a searchg result
![screenshot of tagname](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/6b.png?raw=true)
 
 3. On the left side of the screenshot, you can see a field called a tag - which usually has all the tags displayed in the search and also the field called tag::Eventcode 1 that is for the eventcode i just created (login). alos in the Events, we can see EventCode= 4624 with "login" beside itas a tag.
 ![screenshot of eventcode tag](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/6c.png?raw=true)
 
 4. I ran a search string of all the login report with my account, for context my computername is blacknoir. tag=lpgin will refrence the eventcode=4624. This search report will also parse if you add **Account_Name ="your email"
**. 
 
    ![screenshot opf search acctname](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/6d.png?raw=true)

    
Another interesting anyone can do relating to tags which i chose not is that you can add a colorcode to an Eventtype.To colorcode an eventype, go to settings then filter event type by owner, click on the event type's name this page on the screenshot will display then you can choose what color you want for that event type. in the search s
 ![screenshot of eventtype colorcode](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/6e.png?raw=true)
 
  
*************

<p align="center">  MACROS IN SPLUNK

*************
 Macros are shortcuts we use in searches, they are svaed off searches that can be ran in a search bar just by typing the name of the Macro with backticks(``).This is vbery practical lonq queries we use frequently.

1. To add Macros in Splunk, Goto settings, advanced search, then you find **search macros**, click on **add new** to create a new macro. 

![](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/7a.png?raw=true)

in a different splunk tab, i have a serach string which i will like to make a Macro
![screenshot of macro serach string](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/7b.png?raw=true)

**This search begins by looking in the web index for events where action=purchase, and then uses the stats command to count the number of purchase events grouped by each host. The addtotals command is then applied with col=t and row=f, which adds a new row showing the total count of all hosts combined, while fieldname="Total" assigns the label for the totals row and labelfield=host ensures the totals appear in the same column as the host values.**

**col=t Adds a column total, meaning it calculates the sum of the count column and displays it as a new row.**
**row=f Indicates do not add row totals for each host.**

The final result is a table that displays the event count per host along with an additional row showing the overall total.


2.After clicking **Add new** to create a new macro, I added the search string to the definition of the new macro being created and titled Macro **"salesmade"**.
![screenshot of macro criteria](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/7cc.png?raw=true)

3. to call macro in a search we backslits `` for eg in a serach string it will be refrenced as:
![screenshot of salesmade macro](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/7d.png?raw=true)

Making another Macro bbut this time this one will have an argument parsed into the Macro

**Making another Macro but this time this one will have an argument parsed into the Macro**

1.After creating new macro, i titled the macro "loglevel(1)" Saved Macro with title(1) because I used one argument ($input$). 
 

![screenshot of macro loglvl](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/7g.png?raw=true)

That bracket would have an argument parsed inside it, it could be a field or a string or an expression for eg: here it is a field INFO

![screenshot of macro w argument](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/7h.png?raw=true)






***********************************************************************************************
<br>
<br>
<br>
<br>
<br>
<br>





 A random screenshot of the search string for calculating bytes from megabytes. I initially was going to use this as a macro but storing here for reference

![screenshot of megabyte calculation](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/7e.png?raw=true)

![screenshot of megabyte calculation result](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/7f.png?raw=true)

The search begins with index=web, which retrieves events from the web index. Next, | eval megabytes=bytes/1000000 converts the bytes field into megabytes by dividing by 1,000,000 and stores the result in a new field called megabytes. Then, | stats sum(megabytes) as "Megs" by file calculates the total data volume per file by summing all the megabytes for each file and renames this total as "Megs." Finally, | sort - Megs sorts the results in descending order, so the files with the largest total data transferred appear first.












 



 
  


 


