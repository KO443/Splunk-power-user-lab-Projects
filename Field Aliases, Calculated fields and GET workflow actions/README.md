<p align="center"> FIELD ALIASES


Field aliases are used in Splunk to keep field names consistent across different indexes. I noticed that IP addresses appear under various field names such as **src** or a different field name depending on the source. To maintain consistency and make searches easier, I plan to create a field alias across all indexes so these values are standardized under a single, uniform field name.


To ensure i can create a consistent field name, i checked the sourcetype of my main 3 indexes by running a search query

![sourcetype of my indexes](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/9a.png?raw=true)

now i know my indexes sourcetypes, i will be making their field Aliases.Top start, i navigate to **Settings**,**Fields**, **Fields Alias** then **Add new**

1. After clicking add new this page opens
