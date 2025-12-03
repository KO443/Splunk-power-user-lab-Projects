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
