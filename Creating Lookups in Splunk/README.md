A lookup is a file that contains static data that is not an index, this could be a CSV of all the PC in an office. They can have data that is being updated to them which in such case we will need a KV store Lookup. For this lab i will only be working with Static data lookup. 

Lookups can also be used to pull information from files during searches.

In this short lab, I will demonstrate how to create a lookup using a search query and how to create a static lookup in Splunk. 

TO start we first go to **Settings, Lookups , Lookup table files,** click **New Look up table file**
![screenshot of new Lookup](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5a.png?raw=true)

 for this lookup i uploaded a csv file titled "peoplesinfo.csv", in the screenshot below, you can see it the third to last row in the screenshot below {open image in a new tab to see in HD}
![screenshot of uploaded Lookup](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5b.png?raw=true)
 
