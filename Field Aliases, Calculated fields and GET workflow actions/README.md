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


