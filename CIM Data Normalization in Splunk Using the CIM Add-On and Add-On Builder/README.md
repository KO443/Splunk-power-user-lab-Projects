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

I edited the permission for this new event type.
![web permission](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100i.png?raw=true)

3. After running a search for the new web event type (for example, index=web host=web1), the events are now highlighted in magenta, confirming that the event type and its assigned color are being applied correctly.
![web magenta](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100ii.png?raw=true)

4. Using the tstats command, I ran a search to count how many events are stored in the **Web** data model. The results show that the **Web** data model contains **20385** events.

![dm count](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100iii.png?raw=true)

Lets see the pivot of **web** Data model in GUI from **settings, Data Models,** then **web** Data Model. when we click on **Pivot** 
![web pivot](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100jj.png?raw=true)

..and then click on Parent data set of **web** we can see it also has the same event count as displayed from the Statistics after i ran the search in step no 4
![web pivot count](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100jjj.png?raw=true)



***********************************************
<p align="center"> Using Splunk Add-on Builder to Manage Source Types

***********************************

1. To install the CIM add on builder, I went **Home** then clicked **Find More Apps** and then i install the Splunk Add-on Builder forn enterprise environment as shown in screenshot below:
<img width="575" height="470" alt="image" src="https://github.com/user-attachments/assets/4113d907-5809-430b-a439-bc8dd7fd0f9f" />

<img width="1576" height="910" alt="image" src="https://github.com/user-attachments/assets/65cdcfe0-7686-4fa2-ad48-07581324ee06" />

2. After installing the Add-on, select **New Add-on** button and then this set up page will open
![createaddon](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100l.png?raw=true)

3. At the top bar, select **Manage Source Types**
![manage sources type](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100m.png?raw=true)

4. After clicking on Manage source types, this page opens and then click **add** , **import from Splunk**
<img width="2541" height="852" alt="image" src="https://github.com/user-attachments/assets/fcee35e0-50fd-4ec5-82ce-c3aeb193f252" />

5. As shown in the screenshot, after clicking **Import from Splunk**, i changed sourcetype to **access_combined** and then clicked **save**. 

![import from splk ](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100o.png?raw=true)

6. on the **Events** column, Events count displays as 39532 for the access_combined source type.
<img width="2540" height="343" alt="image" src="https://github.com/user-attachments/assets/3b13803a-5544-47f7-a7ad-45205676892a" />

7. Using the search we can also verify that the event count for access_combined is the same number 39532
<img width="2521" height="637" alt="image" src="https://github.com/user-attachments/assets/272603b4-38b4-43f8-b4be-8b71b78f874d" />

***********************************************
<p align="center"> Using Splunk Add-on Builder to Map to Data Models to Existings Source Types

**********************************************

1. In the Add-on Builder, I clicked **Map to Data Models** then i clicked **New Data Model Mapping**

![Mapto Data Models, new](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100r.png?raw=true)

2. I gave a name for the **event type**, and assigned the **access_combined** sourcetype and then entered the search string **Index=web sourcetype=acccess_combined **  and then click **save**, i added index of web as it is the only index with the access_combined sourcetype.

![DM mapping name](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/100s.png?raw=true)

3. After i clicked saved on the left side of the screen, all the field names for the event type "Example_for_web2" which has the index of web, access_combined source type. All the field names match my Splunk environment field names for that Index. 
<img width="345" height="917" alt="image" src="https://github.com/user-attachments/assets/3f8177f1-f785-4517-a55f-0dd54a443ee4" />

 - we can also verify it matches the field names in the splunk environment
 <img width="379" height="780" alt="image" src="https://github.com/user-attachments/assets/19183357-f610-41cd-93c7-28bda0fb0a26" />

4. hsdhds
5. gsggsgs
6. 



