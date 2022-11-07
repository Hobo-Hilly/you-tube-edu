# NOTE: This is based on VMWARE!!

This is Pt.2 of the Security Onion Installation
Instructor: Josh Brower
In Pt.1 
- we downloaded the security onion iso
- Verified the image
- created a virtual machine (With the appropriate specs according to your desired deployment mode)
- Installed the Operating System CentOS 7

Now in Pt.2 of the install we are going to ...
1. Log back into virtual machine
2. Run through the security onion setup
3. Let the install happen
4. Rebbot
5. Login a final time to make sure all of the security onion services came up and installed correctly

# So we are now starting part 2 of the install from the login screen of the Virtual Machine we created in the previous session

CentOS Linux 7 (Core)
Kernal 3.10.0-1160.53.1el7.x86_64

localhost login: _
Password:_
Last login: Wed Feb 2 15:59:12 on tty1
[sudo] password for analyst:

uname = analyst
pword = ****                         # This information was determined in part one

It will ask for the password again to run setup. Type it in and hit enter.

# WE ARE NOW ON BLUE SCREEN BORE SCREEN ###
    #BP == Blue Page Background + screen number we are on.


# BP 0

Welcome to Sceurity Onion Setup!
You can ...
Setup uses ...

Would you like to continue?

|<Yes>|                   <No>

select yes with arrows and press enter to continue
------------------------------------------------------------------------------------------
- So while we are here we can choose to configure just the network portion of the security onion or we can run a standard install with iso image. The iso image installation method will have us setup the network portion of the security ontion in addition to the other functions.

# BP 1
                | Security Onion Setup - 2.3.100 |
Select an option 

    Install                 Run the standard Security Onion installation
    Configure Network       Configure Networking Only


    <Ok>                            <Cancel>

Tab over to the <Ok> button and push enter
------------------------------------------------------------------------------------------
This is where we choose the deployment mode we selected in Pt.1 Eval mode for this example
NOTE: This is based on VMWARE!!

# BP 2
                | Security Onion Setup - 2.3.100 |
Choose install type.
See https://docs.securityonion.net/architecture for details.

    (*)EVAL                         Evaluation mode (not for production)
    ( )STANDALONE                   Standalone production install
    ( )DISTRIBUTED                  Distributed install submenu
    ( )IMPORT                       Standalone to import PCAP or log files
    ( )OTHER                        Other install types

    <Ok>                               <Cancal>

Tab to the <Ok> button and press enter
------------------------------------------------------------------------------------------------------

# BP 3
                | Security Onion Setup - 2.3.100 |

Starting in Elastic Stack Version 7.11, the Elastic Stack binaries....
Please review ...
Do you agree to the terms ...
If so, type AGREE to accept the Elastic License and continue.
Otherwise, ...

_AGREE________________________________________________________________________

        <Ok>                             <Cancel>
        

----------------------------------------------------------------------------------------------        

# BP 4
                | Security Onion Setup - 2.3.100 |
Enter the hostname (not FQDN) you would like to set:

so-eval________________________________

 <Ok>               <Cancel>    

 Tab to ok and press enter

--------------------------------------------------------------------------------------------------------

Keeping in mind that we have two virtual NICs attached to the VM

# BP 5

                    | Security Onion Setup - 2.3.100 |
Please select your management NIC: 
(*) ens33  00:0c:29:44:d8:cb    Link UP
( ) ens37  00:0c:29:44:d8:d5    Link UP


        <Ok>                <Cancel>

Select ens33 tab to <Ok> press enter

-------------------------------------------------------------------------------------------------------

# BP 6

                    | Security Onion Setup - 2.3.100 |
Choose how to set up your management interface:
(*) STATIC Set a static IPv4 address
( ) DHCP   Use DHCP to configure the Management Interface

    # Note: use STATIC when at all possible. Because using DHCP you run the risk of a system being shutdown for a while or just off line. If when it comes back up it is assigned a different ip address fromo the DHCP server that will cause problems in the platform itself.


-------------------------------------------------------------------------------------------------------

# BP 7

                    | Security Onion Setup - 2.3.100 |
What IPv4 address would you like to assign to this Security Onion installation?

Please enter the IPv4 address with CIDR mask (e.g. 192.168.1.2/24):
192.168.80.45/24_____________________   # This is my private ip addressing. Yours could look like the example.

    <Ok>            <Cancel>

-------------------------------------------------------------------------------------------------------
#NOTE: We should be entering what makes since for our environment. The examples are just the youtube video
# BP 8

                    | Security Onion Setup - 2.3.100 |
Enter your gateway's IPv4 address:

192.168.8.2_______________________________

    <Ok>        <Cancel>

--------------------------------------------------------------------------------------------------------
Leave the default DNS servers

# BP 9

                    | Security Onion Setup - 2.3.100 |
Enter your DNS servers seperated by commas:

8.8.8.8,8.8.4.4_______________________________

    <Ok>        <Cancel>

--------------------------------------------------------------------------------------------------------
Leave the default DNS search domain default

# BP 10

                    | Security Onion Setup - 2.3.100 |
Enter your DNS search domain:

searchdomain.local_______________________________

    <Ok>        <Cancel>

tab to <Ok> push enter

--------------------------------------------------------------------------------------------------------
# BP 11

                    | Security Onion Setup - 2.3.100 |
Setup will now initialize networking.

Select OK to continue
          <Ok>
tab to <Ok> press enter


--------------------------------------------------------------------------------------------------------
# BP 12

                    | Security Onion Setup - 2.3.100 |
how should this manager be installed?
Standard                This manager has internet access
Airgap                  This manager does not have Internet access

        <Ok>            <Cancel>

High light standard and tab to <Ok> press enter

--------------------------------------------------------------------------------------------------------
# BP 13

                    | Security Onion Setup - 2.3.100 |
How would you like to connect to the Internet?
"Direct" - Internet requests connect directly to the Internet.

"Proxy"
 - proxy the traffic for git, docker client, wget, curl, yum, and various other SO components through a seperate server in your environment.

                        Direct
                        Proxy


        <Ok>                <Cancel>

Select Direct and press ok.


--------------------------------------------------------------------------------------------------------
# BP 14

                    | Security Onion Setup - 2.3.100 |
Running Preflight checks ... 
* making sure that everything will install correctly and we have access to the correct web resources


--------------------------------------------------------------------------------------------------------
# BP 15

                    | Security Onion Setup - 2.3.100 |
Please add NICs to the Monitor Interface:
[*] ens37 00:0c:29:44:d8:d5       Link UP



    <Ok>                <Cancel>

--------------------------------------------------------------------------------------------------------
# BP 16

                    | Security Onion Setup - 2.3.100 |

Choose OS patch schedule.

This schedule will update the operating system packages but will NOT update Security Onion related tools such as Zeek, Elasticsearch, Kibana, SaltStack etc.

(*) Automatic                   Updates installed every 8 hours if available
( ) Manual                      Updates will be installed manually
( ) Import Schedule             Import named scheduled on following screen
( ) New Schedule                Configure and name new schedule on next screen


    <Ok>                    <Cancel>

Leave default tab to ok and press enter


--------------------------------------------------------------------------------------------------------
This is for a Suricada home network variable which we will leave alone 

# BP 17
                    | Security Onion Setup - 2.3.100 |
Enter your hoome network(s), seperatig CIDR blocks with a comma (,):

10.0.0.0/8,192.168.0.0/16,172.16.0.0/12

     <Ok>        <Cancel>

leave defaults, tab to <Ok> press enter


--------------------------------------------------------------------------------------------------------
# BP 18

                    | Security Onion Setup - 2.3.100 |
Choose optional services to be enabled for this installation. Be aware that the more services you enable the more RAM that is required.

[*] GRAFANA         Enable Grafana for system monitoring
[*] OSQUERY         Enable Fleet with osquery           # End-point agent
[*] WAZUH           Enable Wazuh                        # End-point agent
[*] PLAYBOOK        Enable Playbook                     # Writing detection plays
[*] STRELKA         Enable Strelka                      # File analysis framework. Used when tools like 'Zeek' extract files off of the network and pass it over to Strelka for further analysis.


    <Ok>            <Cancel>

--------------------------------------------------------------------------------------------------------
# BP 19

                    | Security Onion Setup - 2.3.100 |
Do you want to keep the default Docker IP range?
If you are unsure, please accept the default option of Yes.

          <Yes>           <No>

--------------------------------------------------------------------------------------------------------

NOTE: The email you enter here will NOT be used for sending and receiving emails. This email address is ONLY used as a username to login to these applications
# BP 20   

                    | Security Onion Setup - 2.3.100 |
Please enter an email address to create an administrator account for the web interface.

This will also be used for Elasticsearch, Kibana, and Fleet.

analyst@marvelonions.com_______________________________________________________

              <Ok>                <Cancel>

tab to ok and press enter

--------------------------------------------------------------------------------------------------------
# BP 21

                    | Security Onion Setup - 2.3.100 |
Enter a password for analyst@marvelonions.com:

********____________________________________

Enter and re-enter password tab to ok and press enter.
# BP 22
----------------------------------------------------------------------------------------------------------

# BP 23

                    | Security Onion Setup - 2.3.100 |
How would you like to access the web interface?

Security Onion ...
If you choose ...

( ) IP                  Use IP address to access the web interface
(*) HOSTNAME            Use hostname to access interface
( ) OTHER               Use a different name like a FQDN or Load Balancer


    <Ok>                <Cancel>


* This typically can trip people up so... lets talk about it. When you go to access the SOC you are going to type in the browser https://<IP address for the manager>
                            <Host name>
# IP
If you selct IP address. When you go to access the web interface of the Security Onion Console you will need to type the IP address into the browser to get to the SOC.

# HOSTNAME
If you select host name. You need to make sure that you go to the /etc/hosts file and add the Hostname you want to use and set it to resolve to the IP address you are using to access the SOC(Security Onion Console)


# How to add a host name to your host file on windows 10.
''
In Windows 10 the hosts file is located at c:\Windows\System32\Drivers\etc\hosts. Right click on Notepad in your start menu and select “Run as Administrator”. This is crucial to ensure you can make the required changes to the file. Now click File > Open and browse to : c:\Windows\System32\Drivers\etc\hosts.

Host File Example
# Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host
        SOC IP           so-eaval
# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost
#   
c:\Windows\System32\Drivers\etc\hosts
''

----------------------------------------------------------------------------------------------------------

# BP 24

            | Security Onion Setup - 2.3.100 |
Would you like to configure ntp servers?
    <Yes>       <No>
tab to <Yes> press enter

----------------------------------------------------------------------------------------------------------

# BP 25

                    | Security Onion Setup - 2.3.100 |
Input the NTP server(s) you would like to use, seperated by commas:
0.pool.ntp.org,1.pool.ntp.org

    <Ok>                <Cacnel>

Leave the defaults. tab to <Ok> and press enter


----------------------------------------------------------------------------------------------------------
So by default all ports are locked down aside from Secure Shell Protocol (SSH) on port 22.
So if you want to be able to access the web interface on 443 || https. you need to run this tool so-allow to allow an IP or an IP range access to that web interface.

NOTE: Even if you can pull up the web interface you still need a valid username and password to login to the security onion.

# BP 26

                    | Security Onion Setup - 2.3.100 |
Do you want to run so-allow to allow other machines to access this Security Onion installation via the web interface?

    <Yes>               <No>

Tab to <Yes> press enter

----------------------------------------------------------------------------------------------------------
Using the YouTube Example again here.
# BP 27

                    | Security Onion Setup - 2.3.100 |
Enter a single IP address or an IP range, in CIDR notation, to allow:

192.168.80.0/24____________________________

    <Ok>        <Cancel>    

Tab to <Ok> and press enter
This means that any ip address on the 80's subnet would have access to the SOC. As long as they had a valid username and password


----------------------------------------------------------------------------------------------------------
This is now a summary page with options we did select and some we did NOT have the option to select.

# BP 28

            | The following options have been set, would you like to proceed? |
Security Onion Version: 2.3.100
Node Type: EVAL
Hostname: so-eval
Network: STATIC
Management NIC: ens33
Management IP: 192.168.88.45
Gateway: 192.168.80.2
DNS: 8.8.8.8, 8.8.4.4
DNS Domain: searchdomain.local
Proxy: N/A
Bond NIC(s):
    - ens37
Home Network(s):
    - 10.0.0.0/8
    - 192.168.0.0/16
    - 172.16.0.0/12
Access URL: https://so-eval
Allowed IP or Subnet: 192.168.80.0/24
Web User: analyst@marvelonions.com
Enabled Optional Components:
    - GRAFANA
    - OSQUERY
    - WAZUH
    - PLAYBOOK
    - STRELKA
Metadata Tool: ZEEK
IDS Ruleset: ETOPEN
Patch Schedule:
Type:auto
OS Package Updates: Open
NTP Servers:
    - 0.pool.ntp.org
    - 1.pool.ntp.org
Elasticsearch Heap Size: 4614m
Elasticsearch Storage Space: 29GB
Logstash Heap Size: 700m
Logstash Worker Count: 125
Logstash Batch Size: 125
Logstash Input Threads: 1

Press TAB to select yes or no.


    <Yes>           <No>

