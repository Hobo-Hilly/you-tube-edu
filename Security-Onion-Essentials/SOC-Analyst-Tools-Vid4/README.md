This is the 4th video in a youtube series 
Title: Security Onion Essentials
Video title: Introduction to Analyst Tools
Instructor: Josh Brower
Summary: In this video we are going to walk through the different tools on the Security Onion Platform that we can use to "Slice and Dice" our data.
NOTE: All logins were decided in previous video
---------------------------------------------------------------------------------------------------------------
Starting this episode from the login screen of our Virtual Machine which looks like

CentOS Linux 7 (Core)
Kernal 3.10.0-1160.53.1.el7.x86_64 on an x86_64

so-eval login: _ 
uname: analyst
Password: ****

# Systems check
[analyst@so-eval ~]$ so-status  | less -R     # check to make all security onion components are up and running

[analyst@so-eval ~]$ so-test                  # Will replay network traffic to our security onion instance

* When running so-test make sure you are connected to the interenet. 
* If is ok to see SOME failed packets, just so long as we have SOME successful ones.

[analyst@so-eval ~]$ so-test

-----------------------------------------------------------------------------------------------------------
1. Pull up your browser and Type the IP address || https://so-eval + enter 

NOTE: That during setup it asked how we wanted to connect to the web interface. We selected USERNAME. So AFTER we go to our host file on our local machine and set the HOSTNAME to resolve to the IP we are operating from. THEN we have the luxury of just typing https://<Hostname> instead of hand jamming the IP addr every time.
- You should now be on the security onion Login Screen/ Web Interface

2. login with the creds we created in the setup phase

UNAME= analyst@marvelonions.com
PASS= ****

3. We are now in the SOC (Security Onion Console)

    There is a menu off to the left that we are going to go over.
= SECURITY ONION             # Overview-Administrator are modules/components hosted INSIDE the SOC
--------------------
^ Overview
^ Alerts
^ Hunt
^ Cases
^ PCAP
^ Grid
^ Downloads
^ Administration
----------------
Tools                       # Kibana-Navigator are SEPERATE from the SOC and will open a new window
 Kibana >
 Grafana >
 CyberChef >
 Playbook >
 FleetDM >
 Navigator >  

NOTE: You can find your VERSION of Security Onion on this Overview Screen
# Overview 
This is where we can find 
    Online Help
    Cheatsheet
    TRAINING***
    Alerts
    Hunt
Customize This Space!
    markdownguide.org***
To customize this content, login to the manager via SSH and execute the following command:

$ sudo cp /opt/so/saltstack/default/salt/soc/files/soc/motd.md /opt/so/saltstack/local/salt/soc/files/soc/

follwed by the Security Onion restart command

$ sudo so-soc-restart

On the right hand side there is the blank avatar showing who is currently logged in. 
    On the Drop down
        - Dark Mode
        - What's New
        ? Help
        - Cheat Sheet
        i Blog
        - Settings
        -> Logout

# Alerts
    - Shows all of the Different alerts coming in
# Hunt
    - Used for AdHoc Hunting
# Cases
    - Allows you to create and managae cases and track your investigation
# PCAP
    - Allows you to drill down into a PCAP file
# GRID
    - This will show you all of your active grids as well Username IP addr, Version, Uptime, Status, etc
# Downloads
    - Allows us to access your downloaded tools
        Elasticsearch Utilities
        Wazuh Agents
        osquery Packages and Configs
These will all be relative to YOUR specific instance of the SOC Security Onion Console

# Administration
    Shows the different users on the system
    Under the settings tab you can change your Password

--------------------------------------------------------------------------------
TOOLS

Kibana from Elastic
 1. Click on kibana
 2. Login w/ username and password
 should be the same one you login to the SOC with
analyst@marvelonions.com
****
3. We should now be at: Dashboard > Security Onion-Home
At the top of the page going from left to right.
- - - - - - - - - - - - - - - - - - | - - - - - - - - - - - - - |- - - - - - - - - - - - - - - - - - - - -
Security Onion-Navigation     ***   | Security Onion-All Logs   | Security Onion Logs over time
                                    |                           |
Home                                |       12,278              |
                                    |       count               |       GRAPH
Event Category                      |                           |
Alert|File|Host|Network             |                           |
                                    |                           |
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

- On the bottom left of the dashboard is a pie chart with a SOC overview


- On the bottom Right half are 3 sub-menus 
    Security Onion- Dataset   |  Security Onion-Modules | Security Onion-Log Count By Node
^ Export                      |^ Export                 |^ Export
Dataset  ^  Count  ^          |Module  ^  Count ^       |Node ^    Count ^ 
______________________________|_________________________|_______________________ 
conn            3,211         |zeek       7,868         | so-eval     8,274  
syscollector                  |ossec                    |
http                          |suricata                 |
file                          |osquery                  |       
dns                           |strelka                  |
alert                         |                         |
dce_rpc                       |                         |
irc                           |                         |    
weird                         |                         |    

* There should be a count on everything

Grafana
- This page is loaded with graphs
- it is focused on the overall health of your security onion GRID
- Scroll down
- You can change the time values as well

CyberChef
- Super great analyst tool for manipulating data during an investigation
- Decode/Decryption
- Pull out URL's from a Binary file
- defang URLs before sharing 
    (Defanging a URL ensures that users must make a deliberate decision to visit the intended destination by copying and pasting the URL into their browser address bar. )

Playbook
- Allows you to create rules using sigma and then put them into production

fleet
- used with osquery
- This is the management platform for your osquery agents
1. Login with same creds we login
analyst@marvelonions.com
****
2. View all hosts -->
This will show you how many onions you have enrolled right currently 



Navigater(AKA Attack Navigater)
- This is a simple web application that gives an overview of the MITRE ATT&CK framework
- Shows all the different tactics attackers might use.
- This is typically used in conjunction with Playbook to get an idea of your overall COVERAGE in the environment you are deployed to.
