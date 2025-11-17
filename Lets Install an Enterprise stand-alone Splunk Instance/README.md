In this repository, I will download Splunk Enterprise directly from the official Splunk website and extract the installation package.
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
*In Splunk, we will *

The benefit of these two add-ons is that the Cisco WSA add-on cleanly parses and structures web proxy logs for better visibility into user web activity, while the Unix & Linux add-on collects and normalizes system logs and performance metrics to make server monitoring easier and CIM-aligned.

