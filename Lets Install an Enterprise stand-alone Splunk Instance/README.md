**In this repository, I demonstrate the setup and configuration of Splunk Enterprise. This includes downloading Splunk Enterprise from the official website, extracting the installation package, installing two add-ons, uploading raw data, creating indexes, and assigning sourcetypes to each uploaded file.**
<br>
<br>
<br>
Splunk Enterprise includes a 60-day free trial. After the trial expires, you can still search your data, build dashboards, create reports, write SPL queries, and continue hands-on practice. All previously indexed data remains accessible. The main limitations after the trial are the loss of scheduled searches, alerts, user accounts, and certain enterprise-level features.
<br>
<br>
<br>
This lab begins by downloading and installing Splunk Enterprise, followed by downloading tutorial mock data that will be used as indexed data throughout the exercises.
<br>
<br>
<br>
To download the Splunk ZIP installer:
<br>
Create a Splunk account.
<br>
Go to your Splunk account dashboard.
<br>
Under “Free Trials & Downloads” or “Splunk Platform,” select Splunk Enterprise.
<br>
Choose your operating system and download the installer.
<br>
<br>
After installing splunk and setting up your username and password, the login page is ready and it looks like this 
![Screenshot of Splunk login](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1a.png?raw=true)
<br>
<br>
From here i will still have to dowload the raw data which i will use for my splunk project, the data is is splunks website and i will download 2 splunk add ons from Splunk and then i will add all these raw data to splunk in this page.
<br>
<br>
To download Splunk’s training data for use as mock data in this lab, go to Splunk’s website and search for “search tutorial.” The tutorial files can be difficult to locate, but these are the correct training datasets to download.
<br> 
<br> 
From the screenshot below, i dowloaded tutorialdata.zip file which is vital for this project and the prices.csv.zip which will come in handly for a Dashboard project later in this repo.
![Screenshot of download search tutorial](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/screenshotoftutorial.png?raw=true)
<br> 
<br> 
After downloading the tutorial data zip. You unzip the file and it has our practice data which conians files: www1,www2,www3,cisco iron port  and a mock data.
![screenshot_ of practice data](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/practice%20data.png?raw=true)
<br> 
<br> 
now i will be downloading 2 cisco addons to my splunk emvironment
<br> 
<br> 
In Splunk, at the top left,go to "find more apps"
![screenshot_ of findmoreapps](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1b.png?raw=true)
<br> 
<br> 
install these 2 add ons:
<br> 
<br>
![screenshot_ of cisco wsa addon](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1c.png?raw=true)
<br> 
<br>
![screenshot_ of cisco unix &linux addon](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1d.png?raw=true)
<br> 
<br>
The benefit of these two add-ons is that the Cisco WSA add-on cleanly parses and structures web proxy logs for better visibility into user web activity, while the Unix & Linux add-on collects and normalizes system logs and performance metrics to make server monitoring easier and CIM-aligned.
<br> 
<br>
- In Splunk,go to 'Settings', then 'Add data' and then select 'Upload'
- the host field name field should be the title of the raw data for eg: 
![screenshot of host field name](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1F.png?raw=true)

- we first upload www1, then www2 and www3. these 3 raw files should be created with an index of 'web' and their source type should be 'access.log' and we upload the same file again assigninh index of 'security' and source type'linux_secure'.
- this will take some minutes because the each file from www1 to www3 will be uploaded twice
<br> 
after these processes the review of each raw data before you submit will look like this

-www1
![screenshot of www1 review](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1F.png?raw=true)

-www2
![screenshot of www2 review](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1K.png?raw=true)
![screenshot of www2 review](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1L.png?raw=true)
-www3
![screenshot of www3 review](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1M.png?raw=true)
![screenshot of www3 review](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1N.png?raw=true)

After uploadinh these raw data, i will upload Cisco iron Port file and change source type to 'CISCO:WSA:SQUID', this is where extension comein handy to correctly parse this data. 
![screenshot of cisco source type](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1o.png?raw=true)
![screenshot of cisco review](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1p.png?raw=true)
<br>
<br>
Now i have uploaded all my practice data and created my indexes. We will do an SPL serach to see all our indexes, host, source type and source.
- this search shows all our 4 hosts (www1,2,3 & cisco iron port), our 3 indexes (web,security,cisco), 3 sourctypes (access_combined, linux_secure,cisco wsa) and 3 sources
- performed an SPL search using the time range 'all time' so i can see all my slected fields (data that i parsed into mysplunks disk so far)
![screenshot of index all time](https://github.com/KO443/Splunk-lab-Projects/blob/main/Images/1q.png?raw=true)
