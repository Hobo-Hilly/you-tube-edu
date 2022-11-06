This is from a YouTube series called the Security Onion Essectials. A very powerful blue team tool used for network monitoring in a bevy of different environments. Corporate production all the way down to small medium Business/ Joe Schmoe at home with his at home personal family netwrok.

# NOTE: This tool requires a fair amount of knowlege in networking and general computer science concepts.


"I created this platform back in 2008 to provide a free and open platform for you to peel back the layers of your enterprise and make your advasaries cry." - Doug Burks

Todays SOC(Security Onion Console) has been downloaded over 2,000,000 times. (02/2022)
It is uesed all around the world for
    -Threat Hunting
    -Enterprise Security Monitoring
    -Log Management

- Josh Brower has added Several new useful features over the years



# Video 1 Introduction
Instructor: Josh Brower

In order to "make our advasaries cry" we require a High level of visability into our infrastructure. As well as an ability to slice and dice our way around the data that High Visability brings. That's where this course comes in.

GOAL: Get a solid grasp on the "The Secruity Onion 2" and how it works.
These are the Names and titles of ALL of the videos associated with this series at the time I am writing these notes. 11/06/2022

# Series syllabus and what to expect!
1. Introduction to Security Onion
2. Security Onion Installation Pt.1
3. Security Onion Installation Pt.2
4. Introduction to Analyst Tools
5. Alert Triage and Case Creation  (Workflow #1)
6. Ad Hoc Hunting  (Workflow #2)
7. Dectection Engineering (Workflow #3)
8. Course Wrap Up


# 5. Alert Triage and Case Creation (Workflow #1)
EX: 1. Login to Security Onion
    2. Look at Alert queue and you Triage to see if this is a legitamit threat or not
    3. If YOU decide it is an issue. YOU escalate it to a "Case"

# 6. Ad Hoc Hunting  (Workflow #2)
You don't start with an Alert here. This workflow starts with a question or a hypothesis
EX: 1. Form hypothesis || Question
    2. Go hunt for the answer


# 7. Dectection Engineering (Workflow #3)
This is the process of developing new detection strategies. We will be learning how to do this with in The Securoty Onion itself.

======================================================================================================

1. Supporte Operating Systems
    CentOS, Ubuntu

NOTE: Almost everything with in the security onion with respect to infrastructure uses docker containers. This allows them to support installations on wither centOS || Ubuntu

Salt allows us to orchestrate and manage all of the different docker containers and the configurations associated with them.

2. Infrastructure
    Salt,Docker,Elasticsearch,Redis,Logstash,Filebeat,Grafana

# How does Salt work?
With in the Salt configuartion file we define a state we want the system to be in. i.e. 
- We want docker to be installed with this kind of configuration. 
- We then point Salt at that configuration file and it applies that state.
- It goes out and applies the settings/ does everything we have asked it to do/setup
- Every 15 minutes Salt reaches out to check and make sure the machine(s) are in the state we specified

Elasticsearch
    This is used to store the data.

Logstash/ Filebeat
    Used for shipping the logs as well as some parsing

Redis
    Used for cueing up data

Grafana
    This is a tool that allows you to visualize different performance aspects to the Security Onion


On top of the Infrastructure stack we have the applications that actually generate the Network and Host data.


3. Network & Host Data
Host Tools    
    Wazuh - A Fork of OSEC. Host Intrusion Detection System. Allows you to ship logs from your endpoint and generate alerts based on data that is has seen.
    
    Osquery - Endpoint Agent. Focuses on allowing you to run queries against your endpoint. Live || Scheduled. It also allows you to write those queries in a SQL syntax. 
    
    Beats -  Winlogbeats or any of the other beats family. Winlogbeats reads from one or more event logs using Windows APIs, filters the events based on user-configured criteria, then sends the event data to the configured outputs (Elasticsearch or Logstash). Winlogbeat watches the event logs so that new event data is sent in a timely manner.

Network Tools
    Steno (This is our packet capture util)
    Google/stenographer
GitHub - google/stenographer: Stenographer is a packet capture solution which aims to quickly spool all packets to disk, then provide simple, fast access to subsets of those packets. Discussion/announcements at stenographer@googlegroups.com.
    
    Suricata
    Generates alerts based on the network data that it's seen
    
    Zeek (Formely known as BRO)
    Generates connections logs
    Generates metadata about the network data it has seen
    Also extracts files from that network data

    
    Strelka
    Runs file analysis on the extracted data from Zeek
    Can also use yara to do some signature matching




These tools allow us to pivot around to these different data types as well as slice and dice it

4. Analyst Tools
    SOC(Security Onion Console)
        - This is the Web interface that allows us access to all of the other tools. Which includes 
        Alerts & Hunt
    
    Elastic Kibana
        - Allows you to visualize your data using dashboards.

    Cases
        - Component w/n the SOC(Security Onion Console) itself which allows us to escalate an alert or event inside of the security onion and create a Case. This allows us to track the investigation all the way to completion.
    
    CyberChef "And if you dont know, now ya know, ... " 
        - Super sick nasty tool for pentesters, network admins, security professionals etc ... 
    
    Playbook
        - Allows you to create detection plays based on sigma signature sigma rules

    FleetDM
        - Part of osquery that allows you to run live quieres or scheduled quiered against your osquery endpoints.

    Navigation
        - This is a sick nasty application that MITRE puts out for us lucky ducks! 
        - This gives us the ability to visualize our coverage for the Mitre attack framework across our environment/enterprise

Christmas has come early!!
- All of the previoulsy mentioned tools above are $FREE.99./ Free and open source.
-  Allows us to really fine tune the application(adding to it) for my unique environment

Use Cases & Deployment Modes

