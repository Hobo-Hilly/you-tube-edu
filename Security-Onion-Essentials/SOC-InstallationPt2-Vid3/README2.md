This is the second part of the installation notes.
After you have let the setup complete you will be starting from another blue screen. We will now go back to BP0
---------------------------------------------------------------------------------------------------------------

# BP 0              

        | Security Onion Setup - 2.3.100 |
Finished EVAL installation.

Accedd the web interface at: https://so-eval

Press ENETER to reboot.

    <OK>

NOTE:
If there is an error there will be instructions of where to find logs of the error.
If there is an error please STOP go back and re-run installation/setup. DO NOT try to use the system as is. As it is missing packages it will not be able to be tuned correctly.

---------------------------------------------------------------------------------------------------------------
After reboot

CentOS Linux 7 (Core)
Kernal 45....

so-eval login: analyst
Password ****
Last login ...

Access the Security Onion Web interface at https://so-eval
(You may need to run so-allow first if you haven't yet)

[analyst@so-eval ~]$ sudo so-status | less -R
[sudo]password for analyst: ****

Looking for all green! : )

This will check to make sure all the utilities installed correctly and are up and running
$ uptime            # gets machine up time
