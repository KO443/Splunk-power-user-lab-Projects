<p align="center"> Downloading the CIM App in Splunk


**************
CIM stands for **Common Information Model**, and it is is used to normalize data in Splunk. This means it provides a standardized framework for how all data sources should be structured so that fields follow consistent naming conventions across different indexes and sourcetypes. As a result, all incoming data can be searched in a uniform way throughout the Splunk environment.
<br><br>
in this Long lab, I will downloadthe CIM app and make some data CIM-Compliant using the **CIM Add-On Builder**, i'll begin this  hands-on Lab by installing the CIM app in Splunk.

1. Before Installing CIM, I first went to **Settings**, then **Data Models** to show that my Splunk environment currently contains only two data models, both of which are default models that come preinstalled in Splunk.

![sc of datamodels](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100a.png?raw=true)

2. To download the CIM app, start on Splunk’s home page, click **Apps** in the top-left corner, and then select **Find More Apps** to browse the available add-ons. See my steps in the screeshot below

![cim install](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100b.png?raw=true)
![cim installing](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100c.png?raw=true)

3. After installing the CIM App, Just like i did in step number 1, go to **Settings**, then **Data Models**, and then we can see there are 29 new Data Models from the installed CIM.

![newly installed DM](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100d.png?raw=true)

*******************************************
<p align="center"> Creating  a new Event Type of web based on new Data Models from the CIM App

********************************************
1. Lets go into into the Data Model of **web** (one of the newly installed Data Model from the CIM App)

![webDM](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100e.png?raw=true)

As shown below, web Data Model already has predefined Macros ie (``cim_web_indexes`) and we can see it has child datasets of proxy and storage. 
  
![web DM macros](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100g.png?raw=true)

2. Now I will create tags for the data that should be mapped to a Data Model. To do this, I went to **Settings, Event Types, Create New Event Type**, which opens the event type configuration page. I created a new event type, gave it a descriptive name, and assigned it the tag web. I also selected the color magenta,with a high priority just because this is a Lab. which helps visually distinguish this event type in the search results, making it easy to identify events that belong to the web category.
![eventype](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100h.png?raw=true)

I edited the permission for this new event 

3. jdjd


4. hdhd
5. kdskdk
