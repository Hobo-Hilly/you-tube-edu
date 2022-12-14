This is the 5th video in a youtube series 
Title: Security Onion Essentials
Video title: Alert Triage and Case Creation
Instructor: Matt Gracey ( Engineer at SOC)
Summary: We are goig to go over how to use the 1st Workflow in Security Onion platform.
- We are going to look at alerts from the SOC
- We are going to triage them 
- We then determine which ones need further investigation
- Dismiss some FALSE positives
- Escalate one alert to case using the case management tool
- So we are going to take a look at some data to see how you can manage things during an investigation
-------------------------------------------------------------------------------------------------------------





AFTER LOGGING IN to the Security Onion Console web interface
From the Security Onion Console Overview Page

Workflow #1

1. Select Alerts from the left hand side menu

- We are now on the alerts page which is a central clearing house for all of the alerts raised by the various components with in the Security Onion Platform
- Assumtion is you as an analyst will be checking this regularly to determine which Alerts need to be escalated to a case and those that can be ignored

2. Walk around

- At the top of the Page is the Options drop down
    This controls how Alerts are presented to us in this interface

# Acknowledged: 
Acknowledged Alerts are alerts that have been evaluated and dissmissed by either yourself or another analyst with a username and password to the SOC

# Escalated: 
Escalated Alerts are alerts that you or another analyst decided required further investigation. So they have been escalated into the case management platform.

# Automatic Refresh Interval
Allows you to have the Alerts on the SOC refresh while you are working on other things

# Time Zone
- This allows us to set the Time Zone we want the alerts DISPLAYED in.
- By default data is captured in UTC and then displayed according to the time zone settings in your browser.   
- However, if you would like to change that you can do that right here. And the timestamps of the various data your looking at will update accordingly.


RIGHT SIDE OF SCREEN
The top right hand corner of the screen displays Total Number of Alerts currently all together. There can and may be duplicates.

    Default (relative) time display is Last 12 hours. you can change it from the drop down menu. Days/weeks/months/minutes/seconds/

    You can change it to Absolute time as well by clicking on the clock icon. You then fill out the Calander style clock with an exact date and time you would like to pull from.

LEFT SIDE OF SCREEN
- So by default data is displayed...

Group By Name, Module is the default search critieria
Name: the rule name. What is the name of the rule that caused the alert to fire
Module: Which component of the Security Onion Cause the Alert raise

# How to switch Search critieria?
Scenario: I want to see which IP addresses are raising the most alerts?

1. Click on the Magnifying Glass
2. Select Source IP
* you can select
    Sensor, Source IP/Port, Destination IP/Port,Name
    Source IP,Name
    Source Port, Name
    etc ... 
    ungroup ** ( this will just show ALL alerts indiviually and RAW)

The Grouping Name, Module is a pretty good place to start an investigation.

# What if I only want to see High Priority Alerts?
Method 1
- click the 'event.severity_label ^' label all the way to the right until it shows you high
Method 2
- Left click with mouse on 'high' in the severity column. 
- Select Include
- Now this will add our search critieria to the main search filter above.
 So it will show 

        BLUE                            RED                RED                          RED
|event.severity_label:"high" X ||  Group: rule.name X || Goup: event.module X ||Group: event.severity_label X |

 So we are search by Rule name, Event Module, and ONLY event severity HIGH :)

 # What does it mean if an alert has more than 1 count.
This means that multiple pieces of network traffic match the same signature


3. Under the Filter names the information is broken into columns

# Count                  rule.name                         event.module                event.severity_label
   11                  ET P2P bitTorrent peer sync           suricata                          high

- If you would like to analyze you can click on the rule.name and select drill down || click on the number of alerts right next to it. 11 in this example
- You should now see how many times this particular rule has fired
- So you should be looking at 11 pieces of Identical traffic

# How to clear known good traffic.
Scenario: lets say this is known good traffic.
The sourece IP was my network monitoring solution, the destination IP was my core router. Which means I expect SNMP lookups to be happening there and we want to clear this alert.

Ex:
# Count                  rule.name                         event.module                event.severity_label
   8                    SNMP Public Access Rule              suricata                        Medium

- There is a bell Icon on the far left of EVERY alert. Press that bell icon and the notification will clear.

NOTE: If you have an Alert like this that keeps coming up and wasting your time. Best course of action is to TUNE that rule. That is beyond the scope of this video but we will be covering it later. Even if this series doesn't.

Tuning a rule could be ignoring an IP out right all the way to turning off a specific rule for a specific IP

------------------------------------------------------------------------------------------------------------
We are now going to walk through a piece of traffic that needs more attention sooner then later.
Ex:
# Count                  rule.name                         event.module                event.severity_label
   9             ET MALWARE Zbot POST Request to C2          suricata                         high

General speaking, if you see a POST request to a C2 you are dealing with a compromised endpoint that is already fairly far down the attack chain.
A piece of malware has been installed on it. Persistence at least initial access has been established and it's reaching out to its C2 for further details/instructions

1. Click on the number 9 for "Quick Drill Down"

- from this screen if we want more details. Click the > button on the side of the Bell Icon
This will display all the metadata about this Alert

2. Scroll Down 
    rule.rule 
This is probably the first thing you want to look at. Tells us what characteristics the traffic had that it matched and fired the alarm.

    network.data.decoded
This will show you a snippet of the traffic that caused the alert to fire.

3. Click on the data displayed in network.data.decoded
    Left Click
    select actions
    select PCAP
This opens up a new browser tab and displays the full pcap for this traffic

On this page....

# What if I want a transcript of the information?
-Select the Burger Menu in the middle of the screen. Next to HEX
-This displays everything. To clear HEX information Slect HEX in the middle of the screen
-And now I can see a transcript of just this connection

# How do you escalate an Alert?

4. From the alerts tab...
- Click on the "!" exclamation point in a Triangle. Which is the escalate button. (Blue)
- Select "New Case"

Now we need to open the "Cases" tab from the left side menu
 
# Cases
This tab shows us all of our open cases. We can now use this tab for a central point of operations on any case we have.

1. click on the binoculars icon
after clicking you will see ...
by default the title will use the rule name of the alert that was escalated.


ET MALWARE Zbot POST Request to C2          (Titll. Click to Change)

review escalated event details in the Events tab below. Click here to update this description

|Comments | |ATTACHMENTS|  |OBSERVABLES| |EVENTS| |HISTORY|

--------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------
# After name change looks like ...

Potential ZBot Infection on 192.168.3.65         

review escalated event details in the Events tab below. Click here to update this description

|Comments | |ATTACHMENTS|  |OBSERVABLES| |EVENTS| |HISTORY|



OFF to the Right side of the Screen... We have some Case Attributes
                                                                            Summary
                                                                            Assignee: yourself/co workers


                                                                            Status
                                                                            new

                                                                            Details  ^ 
                                                                            
                                                                            Severity:
                                                                            high
                                                                            
                                                                            Priority:
                                                                            0
                                                                            
                                                                            TLP:
                                                                            traffic light protocol
                                                                            unknown

                                                                            PAP:
                                                                            Permissable Actions Protocol
                                                                            
                                                                            Catagory:
                                                                            <pick a drop down/make own>

                                                                            Tags:
                                                                            <Where infected endpoint is. name of infected network/Department>

* TLP
Traffic Light Protocol
That's how much information thats in this case that you are allowed to share and with whom.


* PAP
Permissable Actions Protocol
- During remediation this is the list of actions that are plausable/allowed. i.e. what can you do about this case?

# Comments
Notes so that multiple analyst can work cases


# Attachments
Attachments is for attaching files to the case.
EX:
Lets say you have a procedure that says you must take a screen shot of the device after the malware has been removed you could upload that screen shot here.

# OBSERVABLES
These are individual artifacts that come up in the investigation

# EVENTS
These are the events in the Security Onion that have been escalated to a case.
This means they have been copied from the security onion database INTO the CASES database to be retained as 
evidence for this case.

- If you click on the carrot to the left of the timestamp if expands details
- You can click the eyeball to the left (where the carrot would be) of the IP address and add it to observable
# What if I want to add a source IP and or a Destination IP to the Obseravbles tab?
After expanding details in the EVENTS tab
1. Select the eyeball to the left of the source IP | fill out and click save
2. Select the eyeball to the left of the destination IP | Fill out and click save

Now both IP's are in the observables


# History
Shows a full history of the case.
Any changes made. Who made them, When they made them.
For audit purposes
---------------------------------------------------------------------------------------------------------------
STATUS: up to this point we have added a case to our case management system that says we have a potential Zbot infection on this '192.168.3.65' machine. We have added a source IP and a Destination IP to Observables.

# Whats the next move? 

Now would be a good time to pivot back to alerts and do a little more investigation. A good idea would be to switch back to the alerts tab. Find the source IP. Click it and select only

So now in the ALERTS tab we will only see Alerts involving the ip addr '192.168.3.65'

Upon further investigation we find 

Ex: ALERTS tab
# Timestamp                             rule.name                     event.severity_label  Src.ip      Src.port
2022-02-01 15:00      ET POLICY PE EXE or DLL Windows file download HTTP    high         188.72.243.72     80

1. click on alert and select PCAP
2. Viewing the PCAP shows that it is sending some sort of malicious executable
3. So the POST request to /kartos/youyou.php HTTP/1.1 looks sketchy
4. go back to alerts
5. click on the IP addr
6. Selec HUNT

HUNT: This allows us to look at all of the information in the security onion instead of just the things that raise alerts

-------------------------------------------------------------------------------------------------------------
# HUNT
We are now on the HUNT page
- You will see that we are now Hunting the IP we selected
- From this screen we want to focus on the file from zeek. located at the bottom of the page ...
- click on 'file' under the "even.dataset" column
- Select Include. This will add the file to our query

STATUS: So now our query says: Anything with 188.72.243.72 AND data about files coming to or from that IP

In the HUNT tab in the file.mime_type we happen to see two executable files which were downloaded to our endpoint 192.168.3.65

We can select the Carrot on the left of one of the two executable files which opens up details
- scroll down to file.analyzer
    This shows that in this example zeek has analyzed it, pulled Hashes, extracted the executable information.
    It has also saved a copy under 'file.extracted.filename' for further review

- for quick actions. click on the hash value in the 'hash.md5' row
    go to actions
    select viruse total
    After viruse total opens we see in this example that 60/65 vendors have tagged this hash as malicious

Now armed with this information we can go back to the HUNT tab
    Click on the '!' exclamation point in the triangle\ Escalate button
    We can now attach this to our Potential Zbot Infection case

To CONFIRM we can go back to the CASE tab
    Go to EVENTS
    Refresh
    you should now see the zeek file we just attached to the case
    we can open it up
    scroll down to the MD5 hash and add it as an observable
    Now if we pop over to Observable we will see the MD5 hash we just added

STATUS: We now have the malicious IP server and the malicious executable all in one place for this case

We could continue the investigation in two ways
1. go back to the alerts tab and check other alerts generated by this source IP and look for other malicious traffic coming from it.

||

Or we can HUNT for IOCs indicators of compromise. Directly from the observables window using the Cross hair Icons.

 i.e. If I wanted to see anywhere else in my environment that the malicious file has shown up. and anywhere else in my environment that this malicious IP has shown up. Just click the crosshair icon in the OBSERVABLES tab.

Once you click on the crosshairs you'll be able to see any other machines on my network that may have reached out to talk with this malicious IP

# Summary

The Alerts interface acts as a starting point to inform analysts of malicious or problematic events on the network. We can choose to acknowledge and dissmiss the || escalate them into cases for further investigation
Once something is escalated to cases, that can be used to record the details of the investigation including related events, observables, attachments and more


