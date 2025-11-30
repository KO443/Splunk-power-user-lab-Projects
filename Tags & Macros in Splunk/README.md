          
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
 
 4. kldkd
 5. hdhdhdh
 6. hdhdhdh
    



 
  


 


