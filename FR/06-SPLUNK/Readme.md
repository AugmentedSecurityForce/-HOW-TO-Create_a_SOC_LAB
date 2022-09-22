- [SPLUNK REQUIREMENTS](#splunk-requirements)
  - [SIZING](#sizing)
  - [SYSTEM REQUIREMENTS](#system-requirements)
  - [PORTS](#ports)
  - [PERSONNAL RECOMMENDATION](#personnal-recommendation)
    - [HARDENING](#hardening)
  - [NOTES](#notes)
- [INSTALLATION OF SPLUNK (WINDOWS)](#installation-of-splunk-windows)
  - [CHECK THE SPLUNK INSTALLATION](#check-the-splunk-installation)
    - [SUPERVISION](#supervision)
- [INSTALLATION OF SPLUNK (LINUX)](#installation-of-splunk-linux)
  - [WITH GUI](#with-gui)
  - [WITH CLI](#with-cli)
  - [CHECK THE SPLUNK INSTALLATION](#check-the-splunk-installation-1)
- [SEND WINDOWS LOGS ON IT](#send-windows-logs-on-it)
  - [INSTALL SPLUNK UNIVERSAL FORWARDER](#install-splunk-universal-forwarder)
    - [CHECK UNIVERSAL FORWARDER FOR WINDOWS INSTALLATION](#check-universal-forwarder-for-windows-installation)
  - [CHECK ON SPLUNK](#check-on-splunk)
- [ADD DATA TO SPLUNK](#add-data-to-splunk)
  - [ADD DATA FROM FORWARDER](#add-data-from-forwarder)
    - [CHECK YOUR INDEXES](#check-your-indexes)
    - [ADD RECEIVER](#add-receiver)
  - [ADD DATA FROM UPLOADED LOGS](#add-data-from-uploaded-logs)
- [SEARCHES](#searches)
  - [TRAPS AND TIPS](#traps-and-tips)
  - [DATE SELECTION](#date-selection)
  - [TIMELINE](#timeline)
  - [SEARCH MODE](#search-mode)
  - [SEARCH BAR](#search-bar)
  - [FIELDS](#fields)
  - [SAVE AS](#save-as)
- [REPORTS](#reports)
  - [WHAT IS REPORT](#what-is-report)
    - [EXERCICE](#exercice)
  - [EDIT OR DELETE AN EXISTING REPORT](#edit-or-delete-an-existing-report)
    - [EXERCICE](#exercice-1)
- [ALERTS](#alerts)
  - [WHAT IS ALERT](#what-is-alert)
  - [EXERCICE](#exercice-2)
- [DASHBOARD](#dashboard)
  - [EXERCICE](#exercice-3)
- [CHECK SPLUNK HEAL STATUS](#check-splunk-heal-status)
- [SECURITY REQUEST](#security-request)
- [MANAGING USERS](#managing-users)
  - [ROLES](#roles)
  - [USERS](#users)
  - [PASSWORD MANAGEMENT](#password-management)

**DISCLAiMER: this part was write before the project comes. Maybe you will have to make somes minors changes**

# SPLUNK REQUIREMENTS
## SIZING
To help you to define the sizing of your Splunk Server, you can use [Splunk Sizing on AppSpot](https://splunk-sizing.appspot.com/).

![sizing1](/Images/sizing1.png)

## SYSTEM REQUIREMENTS
The official documentation give you the system requirment for Splunk Enterprise on-premises [here](https://docs.splunk.com/Documentation/Splunk/9.0.1/Installation/Systemrequirements)

## PORTS
Don't forget to open ports on your firewall.
The default ports needed are : 
* 9997 for forwarders to the Splunk indexer.
* 8000 for clients to the Splunk Search page
* 8089 for splunkd (also used by deployment server).

if needed more [chech this](http://downloads.jordan2000.com/splunk/Splunk-Common-Network-Ports-v2.0.3.png)

## PERSONNAL RECOMMENDATION
### HARDENING
Your Splunk server will received a lot of important data for your enterprise. I really recommend you to hardened it.

## NOTES
_After 60 days you can convert to a perpetual free license._

![licence](/Images/licence.png)

# INSTALLATION OF SPLUNK (WINDOWS)

For the training we gonna install Splunk on a Windows Server 2022 virtual machine.

* Goes to the [Splunk Site](https://www.splunk.com/en_us/download/splunk-enterprise.html?locale=en_us)
* Create an account
* Download the MSI installer

![install1](Images/Install1.png)

* Read the Licence Agreement
_I know, this seem useless and no one will do, be YOU need ton read it and understand it. It will containt all your enterprise information. You need to know what will be done with your data"_

![install2](Images/Install2.png)

* Accept the Licence Agreement
* For the training we gonna customize options, so press "Customize Options" even if we gonna left default configuration.

![install3](Images/Install3.png)

* Select where you want to install Splunk
* Install Splunk as a local System
* Set the credentials

![install4](Images/Install4.png)

* Launch this install and waiting

## CHECK THE SPLUNK INSTALLATION

After the job is done, try to connect on it : https://127.0.0.1:8000

![install5](Images/Install5.png)
![install6](Images/Install6.png)

Congratulation, you have installed Splunk !

### SUPERVISION
If you go to services.msc you will find a "Splunkd Service" wich have a startup type "automatic" and it must be in running status.
You can monitor this service and status to check your Splunk state.

![service1](Images/service1.png)

# INSTALLATION OF SPLUNK (LINUX)
For this part i will use a Ubuntu 22.04 Desktop computer. It will work with others distributions and a server one, but since i used the VM for other things it will be easier.
## WITH GUI
* Goes to the [Splunk Site](https://www.splunk.com/en_us/download/splunk-enterprise.html?locale=en_us)
* Create an account
* Download the .deb file

![linux1](/Images/linux1.png)

* Goes to your Downloads folder

![linux2](/Images/linux2.png)

* Right Click on it > Open with Other Applications > Software Install

![linux3](/Images/linux3.png)

Click on "Install" button and wait.

![linux4](/Images/linux4.png)

## WITH CLI
* Goes to the [Splunk Site](https://www.splunk.com/en_us/download/splunk-enterprise.html?locale=en_us)
* Create an account
* When you try to download it, check the right upper corner

![linuxcli1](Images/linux_cli1.png)

* Click on "Command Linux Wget", it will give you the command you need to download it.
* _For this section i will use the tgz format_

![linuxcli1](Images/linux_cli2.png)

* Open your terminal
* Goes to your installation folder (/opt for me)
* Paste the command given few steps ago
* Add "sudo" if needed

![linuxcli3](Images/linux_cli3.png)

* Goes to root user
* Extract it with : tar xvzf splunk-9.0.1-82c987350fde-Linux-x86_64.tgz
* Launch it : /opt/splunk/bin/splunk start --accept-license
* Answer the questions

![linuxcli4](Images/linux_cli4.png)

* Try to connect to the link given

![linuxcli5](Images/linux_cli5.png)

![linux5](Images/linux5.png)

## CHECK THE SPLUNK INSTALLATION
By default, Splunk on linux don't run at the system startup.
To make it start, run this command in root : /opt/splunk/bin/splunk enable boot-start

![linuxcli6](/Images/linux_cli6.png)

Restart and check the status : /opt/splunk/bin/splunk status

![linuxcli7](/Images/linux_cli7.png)

# SEND WINDOWS LOGS ON IT
## INSTALL SPLUNK UNIVERSAL FORWARDER
For the training, we gonna install the universal forwarder in default configuration.

* Goes to the Windows computer
* Download the [setup](https://www.splunk.com/en_us/download/universal-forwarder.html?utm_campaign=bing_emea_tier1_en_search_brand&utm_source=bing&utm_medium=cpc&utm_content=Uni_Forwarder_Demo&utm_term=splunk%20universal%20forwarder&_bk=splunk%20universal%20forwarder&_bt=&_bm=e&_bn=o&_bg=1140194278998147&device=c&msclkid=9b23c90e3a1e1e49076eaa1f8968a7da)

![install7](Images/Install7.png)

* Read the Splunk General Terms

* Download the MD5

![install8](Images/Install8.png)

* Open the md5 file to have the checksum : at this time is : 183a09c64537832701320609e665e3e7
* Check your MD5 (Get-FileHash .\splunkforwarder-9.0.0.1-9e907cedecb1-x64-release.msi -Algorithm md5) to confirm you've got the right installer.

![install9](Images/Install9.png)

* Launch the setup
* Read the Licence Agreement

![install10](Images/Install10.png)

* Accept the Licence Agreement
* Select "an on-premises Splunk Enterprise instance" because we have install Splunk on an on-premise server.

![install11](Images/Install11.png)

_Once again, we use the default configuration. Maybe in your company you will use a service account to run the Universal Fowarder._

* Give a username to Universal Forwarder.

![install12](Images/Install12.png)

* Give the server IP or Hostname and the port to the receiving indexer.
_I use the IP because i have no DNS in my lab. We don't have change any configuration during Splunk installation so the port used is 9997_

![install13](Images/Install13.png)

**Why give ip in receiving indexer and not in deployment server ? Because we don'"t have a Deployment server. A deployment server is the server that can send a configuration for your universal forwarder.**

* Launch the install

### CHECK UNIVERSAL FORWARDER FOR WINDOWS INSTALLATION

* Goes to services.msc
* Check if "SplunkForwarder Service" is up.

![install14](Images/Install14.png)

* Check if communication are open with Powershell (Test-NetConnection -Computername Splunk_IP -port 9997)

![install15](Images/Install15.png)

Congratulation, you have installed Splunk !

## CHECK ON SPLUNK
* Go to your Splunk Server
* Goes to Settings > Forwarder management

![forwarder1](Images/forwarder1.png)

You must see your Windows Computer on this page.

![forwarder2](Images/forwarder2.png)

**if you don't see your computer after minutes, try to restart the Splunk Universal Forwarder service, check if the the connection between client and server are ok.**

# ADD DATA TO SPLUNK
In Splunk you can add data by differents ways.
Here we gonna see by the forwarder installed on the Win10 computer and with th upload of a log file.
## ADD DATA FROM FORWARDER
* Goes to Settings > Add Data

![forwarder3](Images/forwarder3.png)

* Select "Forward" at the bottom

![forwarder4](Images/forwarder4.png)

* Add the computer to the selected host and give it a Server Class Name
* Press "Next"

![data1](Images/data1.png)

* Select what you want to monotore, in this case we want to collect te local event log from this computer.
  * Select wich log you want
* Press "Next"

![data2](Images/data2.png)

* Select the index where the logs need to be put.
  * I choose to create a new one named "WinLog_clients"
    * for this, click on "create a new Index"
* Press Review to check and then submit.

![data3](Images/data3.png)

now, you can press "start searching" to try to find your last connection on the client computer.

### CHECK YOUR INDEXES
* Goes to Settings > Indexes

![indexes1](Images/indexes1.png)

* Search the index you create previously

![indexes2](Images/indexes2.png)

**like you see there is no incomming event, you gonna configure it now**

### ADD RECEIVER
* Goes to Setting > Forwarding and reveiving

![receive1](Images/reveive1.png)

* Click to add new receiving

![receive2](Images/receive2.png)

* Add the 9997 port (it's the default one, remember the beggining)

* Wait a few minutes and check your indexes again, you will see new values

![indexes3](Images/indexes3.png)

* Try a quick search ;)

![search1](Images/search1.png)

## ADD DATA FROM UPLOADED LOGS
* Goes to Settings > Add Data

![forwarder3](Images/forwarder3.png)

* Select "upload" in the bottom left corner

![upload1](Images/upload1.png)

* Push the file you want to upload, then press "Next"

![upload2](Images/upload2.png)

* Check how Splunk will read your file, then press Next if everythings is ok
* Select a host field value if needed, and the index wich is gonna be used (left default in the exercice)
* Continue to the end, and start searching on it ;)

![upload3](Images/upload3.png)

# SEARCHES 
Let take a tour on the Search page.

![searchall](Images/search_all.png)

Like you see, there are lot of informations to understand, let's try to clarify them.

## TRAPS AND TIPS
* Field names are case sensitive
* Field value are not case sensitive
* Wilcard is available (used *)
* You can use operators such as AND, OR, NOT

## DATE SELECTION
The first thing to do is to select the data range.

![date1](Images/date1.png)

From here you can chose : 
* Presets (today, last week, last year, last 24 hours, etc.)

![date2](Images/date2.png)

* Relative (beginning of hour, X minutes ago, X weeks ago, etc.)

![date3](Images/date3.png)

* Real-time
* Date range (between 00:00 DD/MM/YYYY and 24:00 DD/MM/YYYY)

![date4](Images/date4.png)

* Date & time range (same but you can choose hour)

## TIMELINE
When you perform a search, Splunk display a Timeline

![timeline1](Images/timeline1.png)

## SEARCH MODE
There are three mode, you will use mostly the Smart Mode.

![mode1](Images/mode1.png)
![mode2](Images/mode2.png)

## SEARCH BAR
This is where you make your request.

![searchbar1](Images/searchbar1.png)

Like i say previously, you can use wildcard character ("*") and operators.
You can mix all !

* You search for username with "Je" on it ? Try Username=Je*
You will find username like Jeanne, Jean, etc.
* You search for connection on the computer named computer1 ? Try eventid=4624 AND computername=computer1
* You search for every connection on computer except the domaincontroller ? Try eventid=4624 NOT computername=domaincontroller
* Remember to use "Search History" ;)

## FIELDS
Fields are availables on the left.
Here you have each fields available in your search.
![field1](Images/field1.png)

Select on field to have informations about it.

![field2](Images/field2.png)

## SAVE AS
In this menu you can choose to save your request as a report, alerte or dashboard.

# REPORTS
## WHAT IS REPORT
Bassicly, reports are saved searches results.
Reports can be scheduled or can be execute when needed.

### EXERCICE
For this part, we gonna used a simply request to find connections failed with account that contain admin
My request is : source="WinEventLog:*" index="winlog_clients" EventCode=4625 AND Nom_du_compte=*Admin*

_Maybe you need to change the "Nom_du_compte" to "accountname"._

* Try your request in search bar
![report1](Images/report1.png)

* Goes to Save As menu and select 
![report2](Images/report2.png)

* Give a title and a description of your report
![report3](Images/report3.png)

* Save and goes to View
![report4](Images/report4.png)

## EDIT OR DELETE AN EXISTING REPORT
* From the Search App, goes to Reports sections
![report5](Images/report5.png)
![report6](Images/report6.png)

Here you can find all existing reports.
* Select the report created few minutes ago.
![report7](Images/report7.png)

From here you can see informations about your report.

* Select the Edit button
![report8](Images/report8.png)

### EXERCICE
We gonna schedule this report for everyday at 08AM to have the connections failed yesterday.
* Select "Edit Schedule"
* Check "Scedule Report"

![schedule1](Images/schedule1.png)

* Configure it.
![schedule2](Images/schedule2.png)

_In this exercice you don't used trigger actions, but I invited you to check what you can when your report is generated (like send an email, launch a script, etc.)

* Save and check again informations about your report.
![schedule3](Images/schedule3.png)

# ALERTS
## WHAT IS ALERT
Alerts are a saved searches than trigger when certain conditions are met.
They can be scheduled or in real-time. In that case, becarefull to not overload your Splunk server.

## EXERCICE
Use the same request as report section and save it as an alert.
![alerte1](Images/alert1.png)

Like you see, you have more informations to give than a simple report.
You will need to give the kind of alerte (scheduled or in real-time), when it must be run (if you have more than 35 connections failed for exemple), and the action.
# DASHBOARD
Dashboard is nothing more than ... a dashboard.
From here you can find lot of information you need.

You can make one for analyst, on for your customers, with differents informations.
If you used always the same requests, need always the same informations, making a Dashboard is a good idea.

## EXERCICE
Use the same command has previously and save it as a New Dashboard called "SOC L1". Because it's for all people in SOC, you must shared it.

![dash1](Images/dash1.png)

_Here we have only one panel, but you can add other panel to this dashboard_

# CHECK SPLUNK HEAL STATUS
When your connected to Splunk, click near the Administrator menu

![status1](Images/status1.png)
![status2](Images/status2.png)

On the left control panel you have the status of each part of Splunk Server.
on the right control panel you have the explaination of each signal.

# SECURITY REQUEST
Splunk give you some security request to used to detect things like brute-force.
Simple goes to [Splunk Security Essential aka SSE](https://docs.splunksecurityessentials.com/content-detail/basic_brute_force/)

# MANAGING USERS
## ROLES
By default Splunk give you some roles, to find or create a new role, go to Settings > Roles

![role1](Images/role1.png)
![role2](Images/role2.png)

From here you can edit or add a new role.
A role can give you permission on Splunk server, splunk request, on wich events ou can see or not, etc.

## USERS
When you installed it, Splunk give you only one user, wich is admin.
A good practice is to create an other administrator account and use admin only in emergency case. This way, if you see admin connection you can see there is a problem ;).

To find the users list and create new one, go to Settings > Users.

![user1](Images/user1.png)

Every user must have a role.

## PASSWORD MANAGEMENT
When you installed Splunk, they only ask for a 8 characters password, no matter the complexity.
You can modify it on Settings > Password management

![pwdman1](/Images/pwdman.png)
