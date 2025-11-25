In this lab, we’ll explore several methods for extracting fields in Splunk, including using the Event actions dropdown, the Fields Extraction menu in the GUI (Regex and Delimiters options), as well as SPL-based extraction techniques using the rex and erex commands
<br>
<br>
In Splunk, we use regex for extracting fields from unstructured data and delimiters for parsing structured data, and we apply the rex and erex commands when performing field extractions directly in SPL.
<br>
<br>
1. One manual way to extract fields in Splunk is through the GUI by navigating to Settings → Fields → Field Extractions → Open Field Extractor. This workflow launches Splunk’s Field Extractor (FX), a guided tool that helps you create new field extractions without writing SPL. It allows you to choose sample events, highlight the values you want to extract, and automatically generates the appropriate regex or delimiter-based pattern. Once saved, the extraction becomes a reusable knowledge object that Splunk applies at search time across matching events.


2. Another way to extract fields is by searching an index for eg: **index=cisco** uand scrolling to the bottom of the Fields tab, where you’ll find the + Extract New Fields option on the left side of the screen.

![Screenshot of extract new fields](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4a.png?raw=true)

3. We can also extract new fields using the **Event Actions** dropdown menu. After running a search, open one of the returned events, click** Event Actions**, and select** Extract Fields** from the dropdown.

![Screenshot of event actions](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4b.png?raw=true)

After selecting Extract Fields, a new page opens where you can choose the extraction method between either Regular Expression or Delimiters. In this lab, I’ll provide a short demonstration of both approaches.

![screenshot of delimeter or RegEx](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4bi.png?raw=true)

When you choose the **Delimiters** method, you can click any of the automatically generated fields (e.g., field1, field2, field3) and rename them. For example, if field3 represents the client IP, you can rename it to **clientip**. After updating the names, clicking **Next** saves the fields with their new labels.

![screenshot of delimeter rename](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4ci.png?raw=true)

Returning to the point where you choose between **Delimiters** or **Regular Expression**, selecting **Regular Expression** (via Event Actions,Extract Fields) leads you to the field-extraction naming step. 

From here, creating a regex-based extraction is simple: highlight the value you want to extract and assign it a field name. For example, in the screenshot, I highlighted the IP address and named it accordingly, and I also highlighted the string **GET** and labeled it as the **method** field, and also highlighted the URL and named it **domain**.

![screenshot of Reg Ex renaming](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4c.png?raw=true)
![screenshot of url rename](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4eiii.png?raw=true)

After clicking **Next**, the following step is to **validate** the field extraction. In this example, my three extracted fields:** IP, method, and domain** are displayed and color-coded, making it easy to confirm that each value was correctly identified. {open image in a new tab to see HD version}
![color coded field extraction](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4d.png?raw=true)

then Click next to save, name the extraction and assign permissions to the Extraction.
![screenshot of save extraction](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4e.png?raw=true)

4.In this part of the lab, I will use the rex command in Splunk to extract fields from the data. The main challenge here is crafting the correct regular expressions (regex) to accurately extract the desired fields. Udemy instructor Hailee Shaw demonstrated how to use this site **https://regex101.com/** an online tool that helps build, test, and debug regular expressions, making it easier to identify powerful patterns for matching text.
<br>
<br>
I entered a search string using rex command in the index of cisco. In this Search string i used regular expressions that will pull emails from raw events and create a field for emails.

![screenshot of erex cmd](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/4f.png?raw=true)

**The regex expression (?<email>"\s+@\s+.com") In this regex, (?<email>...) defines a named capture group called email, which stores the matched content. The \S+ matches one or more non-whitespace characters for both the username and domain parts of the email, @ matches the literal @ symbol, and \.com matches the .com at the end of the email, with the backslash escaping the dot so it is treated literally rather than as “any character.”**



