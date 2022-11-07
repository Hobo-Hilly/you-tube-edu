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

# BP 3
                | Security Onion Setup - 2.3.100 |
Enter the hostname (not FQDN) you would like to set:

so-eval________________________________

 <Ok>               <Cancel>    

 Tab to ok and press enter

--------------------------------------------------------------------------------------------------------

Keeping in mind that we have two virtual NICs attached to the VM

# BP 4

                    | Security Onion Setup - 2.3.100 |
Please select your management NIC: 
(*) ens33  00:0c:29:44:d8:cb    Link UP
( ) ens37  00:0c:29:44:d8:d5    Link UP


        <Ok>                <Cancel>

Select ens33 tab to <Ok> press enter

-------------------------------------------------------------------------------------------------------

# BP 5

                    | Security Onion Setup - 2.3.100 |
Choose how to set up your management interface:
(*) STATIC Set a static IPv4 address
( ) DHCP   Use DHCP to configure the Management Interface

    # Note: use STATIC when at all possible. Because using DHCP you run the risk of a system being shutdown for a while or just off line. If when it comes back up it is assigned a different ip address fromo the DHCP server that will cause problems in the platform itself.


-------------------------------------------------------------------------------------------------------

# BP 6

                    | Security Onion Setup - 2.3.100 |
What IPv4 address would you like to assign to this Security Onion installation?

Please enter the IPv4 address with CIDR mask (e.g. 192.168.1.2/24):
10.0.0.1/24_____________________   # This is my private ip addressing. Yours could look like the example.

    <Ok>            <Cancel>

-------------------------------------------------------------------------------------------------------

# BP 7

                    | Security Onion Setup - 2.3.100 |
Enter your gateway's IPv4 address:

10.0.0.1_______________________________

    <Ok>        <Cancel>

