<p align="center"> FIELD ALIASES


Field aliases are used in Splunk to keep field names consistent across different indexes. I noticed that IP addresses appear under various field names such as **src** or a different field name depending on the source. To maintain consistency and make searches easier, I plan to create a field alias across all indexes so these values are standardized under a single, uniform field name which will be **source_iP**.


To ensure i can create a consistent field name, i checked the sourcetype of my main 3 indexes by running a search query

![sourcetype of my indexes](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/9a.png?raw=true)

now i know my indexes sourcetypes, i will be making their field Aliases.Top start, i navigate to **Settings**,**Fields**, **Fields Alias** then **Add new**

1. After clicking Add New, the configuration page opens. In the Name field, I entered the new field name source_ip. This alias is being created for the access_combined sourcetype, which already contains an IP address field called src, but I intend to create an alias so that src is also recognized as source_ip.
![access_combined field alias](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/9b.png?raw=true)

2. I did the same thing for my cisco index. I named the field alias **source_ip** and i assigned the field alias its sourcetype which is **cisco:wsa:squid**
![cisco sourcetype fa](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/9c.png?raw=true)

3. I did the smae thing for my security index with sourcetyoe linux_secure. 
![linux scure sourcetype fa](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/9d.png?raw=true)

THis is how field Aliases are created, the original field from each index will still appear but a normalized new field **source_ip** will appear in terestingh fields.



****************************

<p align="center"> CALCULATED FIELDS
  
*******************************

I will create a calculated field that calculates bytes to megabytes. in index of web (**index=web**), i will be working with the **bytes** field to create a calculated field called **megs**

1. to start we go to **settings**, **fields,  calculated fields** , and then **add new** and a configuration page will open

![](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/9e.png?raw=true)

I intend to make this Megs calculated field convert bytes to megabyte hence the **Eval expression** **bytes/1024/1024**.
Dividing bytes by 1024 twice converts it to megabytes because it first changes bytes to kilobytes, then kilobytes to megabytes.

2. After Saving the Calculated field, here how to i use it in a search

![search string of megs field](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/9g.png?raw=true)

The search begins with **index=web**, which retrieves all events from the web index. The command stats sum(megs) as megs by file then aggregates the data by taking the sum of the calculated field **megs** (the calculated field i just created) for each file, producing one row per file with its total megabyte size. Finally, **sort - megs** sorts the results in descending order, so the files using the most megabytes appear at the top.


************************************
<p align="center"> GET Workflow Actions

***********************************
GET Workflow can be used to leverage a web resource and send one of your fields in Splunk to that web resource to then gain additional information from it. GET can create HTML links to interact with sites.

1. In this short section of the Lab, i will be using this IP look up (**whois.domaintools.com**)tool for this lab, it is a web resource used to lookup any IP of interest.
   
To start we navigate to **Settings**,**Fieldss** then **workflow actions** and click **Add new** to open the workflow action configuration page

![sc of workflow actions](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/10a.png?raw=true)

2. As shown in the screenshot, I named this workflow action “IP Whois Lookup.” For the label, I used $clientip$, which serves as a token representing the clientip field which is an IP address field in the web index.
 - This token allows the workflow action to automatically pull the IP address from each event and use it in the lookup.
 - For the Action Type, I selected **Link** and entered the lookup URL in the URL field followed by the workflow label as i did in the screenshot.
 -  The Link Method provides two options: GET or POST and for this lab, I chose GET, as shown in the screenshot.
 ![workflow action config page](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/10b.png?raw=true)

3. We can see workflow has now been saved amd it is time tom use it in the Search homepage. {Open image link in a new tab to see HD version}
![Saved workflow](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/10c.png?raw=true)


4. To use this Workflow action in a serach we first search Index of web. We can see already see an IP address in the events. we will use this GET workflow to find who the IP is.
![workflowcation search](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/10d.png?raw=true)

 - In the dropdown (Evnt Actions) of that event with the IP, we can see that whois:$ClientIP$ workflow already grabbed that IP and if we click on the whois:$clientIP$, it looks up that IP adress at the site (whois.domaintools.com) and provides a result.
 - ![IP lookup GET](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/10e.png?raw=true)

result of the workflow action
 - ![IP result of workflow](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/10f.png?raw=true)




