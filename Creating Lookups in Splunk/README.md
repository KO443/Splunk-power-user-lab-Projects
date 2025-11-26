A lookup is a file that contains static data that is not an index, this could be a CSV of all the PC in an office. They can have data that is being updated to them which in such case we will need a KV store Lookup. For this lab i will only be working with Static data lookup. 

Lookups can also be used to pull information from files during searches.

In this short lab, I will demonstrate how to create a lookup using a search query and how to create a static lookup in Splunk. 

To start we first go to **Settings, Lookups , Lookup table files,** click **New Look up table file**
![screenshot of new Lookup](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5a.png?raw=true)

For this lookup, I uploaded a CSV file titled peoplesinfo.csv. After uploading it, I saved the data and adjusted the permissions as needed. In the screenshot below, you can see the file listed as the third-to-last entry. {open image in a new tab to see in HD}
![screenshot of uploaded Lookup](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5b.png?raw=true)
 
To view the lookup, I ran a search using the inputlookup command: | inputlookup peoplesinfo.csv  {open image in a new tab to see in HD}
![screenshot of lookup search](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5c.png?raw=true)
<br>
<br>
After uploading and saving a lookup file in Splunk, the next step is to create a lookup definition. This definition tells Splunk how the lookup should be used in searches by assigning it a readable name, mapping its fields, and setting the appropriate permissions. Without a lookup definition, the file exists in Splunk but cannot be properly referenced or applied in search commands such as lookup, inputlookup, or through automatic lookups. Creating the definition ensures the lookup is fully functional and accessible within your searches.
<br>
<br>
To set a lookup definition, navigate to **Settings**, **Lookups**, **Lookup definitions**, then click **Add new lookup definition **in the top-right corner.{open image in a new tab to see in HD}
![screenshot of lookup definition](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5d.png?raw=true)
adding the lookup definition
![screenshot of adding lookup def](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5e.png?raw=true)
<br>
<br>
<br>
In this part of the lab, I created a static lookup using SPL. I searched the web index and used the table command to display the productId field. I then applied the dedup command to remove duplicate values, ensuring that only unique product IDs were included before exporting the results as a static lookup.
![screenshot of static lookup](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5f.png?raw=true)

This static Lookup can be exported into a csv file by clicking **export**
![screenshot of static lookup export](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/5g.png?raw=true)
