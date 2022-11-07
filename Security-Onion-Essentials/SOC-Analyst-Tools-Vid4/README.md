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

3. 