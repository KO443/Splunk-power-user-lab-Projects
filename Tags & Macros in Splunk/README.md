          
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
    



 
  


 


