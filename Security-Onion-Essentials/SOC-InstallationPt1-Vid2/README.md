Second part of the Security Onion Essentials course
Instructor: Josh Brower
Installation - Part 1
#  HEADS UP!!! THIS DEMO IS ALL IN RELATION TO VMWARE. That is all. Thank you. !!!!!!




# Agenda 
In this episode we will be starting the installation process of the Operating System that is The Security Onion.
1. Download ISO
2. Create virtual machie with required system resources
3. Install The Onion Operating System itself.

THE NEXT VIDEO will include The Security Onion Setup...

Installation Process from start to finish.

1. Go to securityonion.net --redirects--to--- > securityonionsolutions.com
2. Click on Software at the top of the screen
3. Click download now. --- redirects---> github repo
4. Following the instructions from github install instructions...


2.3.181-20221021 ISO image built on 2022/10/21
Download and Verify
2.3.181-20221021 ISO image:

https://download.securityonion.net/file/securityonion/securityonion-2.3.181-20221021.iso


MD5: 9389B35233DCA42AC5061053D772E922
SHA1: 83A162756136198CF1FABE7D94BA1D99650379B2
SHA256: FED4D7B27C16889F9588FE9568B0B10E0DAD551C34619DFED7801F18B1739040

Signature for ISO image:
https://github.com/Security-Onion-Solutions/securityonion/raw/master/sigs/securityonion-2.3.181-20221021.iso.sig

Signing key:
https://raw.githubusercontent.com/Security-Onion-Solutions/securityonion/master/KEYS

For example, here are the steps you can use on most Linux distributions to download and verify our Security Onion ISO image.

# CLI Commands to install and check the integrity of the Security Onion ISO you have downloaded


Download and import the signing key:

wget https://raw.githubusercontent.com/Security-Onion-Solutions/securityonion/master/KEYS -O - | gpg --import -  


Download the signature file for the ISO:

wget https://github.com/Security-Onion-Solutions/securityonion/raw/master/sigs/securityonion-2.3.181-20221021.iso.sig


Download the ISO image:

wget https://download.securityonion.net/file/securityonion/securityonion-2.3.181-20221021.iso
Verify the downloaded ISO image using the signature file:



gpg --verify securityonion-2.3.181-20221021.iso.sig securityonion-2.3.181-20221021.iso
The output should show "Good signature" and the Primary key fingerprint should match what's shown below:



gpg: Signature made Fri 21 Oct 2022 02:11:18 PM EDT using RSA key ID FE507013
gpg: Good signature from "Security Onion Solutions, LLC <info@securityonionsolutions.com>"
gpg: WARNING: This key is not certified with a trusted signature!*****
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: C804 A93D 36BE 0C73 3EA1  9644 7C10 60B7 FE50 7013 *****
Once you've verified the ISO image, you're ready to proceed to our Installation guide:
https://docs.securityonion.net/en/2.3/installation.html


Once you've used gpg to verify the signature on the ISO you just downloaded it is time to move on to the installation guide. 

=====================================================================================================
Once you've verified the ISO image, you're ready to proceed to our Installation guide:
https://docs.securityonion.net/en/2.3/installation.html

There are two ways to install the security onion 
1. Use the ISO image we just downloaded. Most cases this is the quickest easiest method
2. Network Install method
    - Install Ubuntu/centOS
    - git clone on the onion repository
    - Run setup script
    NOTE: The setup script is the same ISO || Network installer

We are going to use the Secuirty Onion ISO Image to install CentOS 7

Installation using Security Onion ISO Image
If you want to install Security Onion using our ISO image:

1. Review the Hardware Requirements and Release Notes sections.

2. Download and verify our Security Onion ISO image.

3. Boot the ISO in a machine that meets the minimum hardware specs.
    Minumin Specs
    Minimum Specs
If you just want to import a pcap using so-import-pcap, then you can configure Security Onion 2 as an Import Node with the following minimum specs:

4GB RAM
2 CPU cores
200GB storage

**For all other configurations, the minimum specs for running Security Onion 2 are:
12GB RAM
4 CPU cores
200GB storage

NOTE: These minimum specs are for EVAL mode with minimal services running. These requirements may increase drastically as you enable more services, monitor more traffic, and consume more logs.

So this portion is going to be about setting up your virtual machine. You can use VMware, Virtualbox, hypervisor and I believe a few others. They should all work fine.
    Create New VM
    Install from Disk/Image
    Select ISO we just downloaded, click continue
    Select CentOS 7 64-bit
    Select Finish and Name == so-eval  #Naming Convention so-<name of iso>
    Select Save
Time to adjust settings
        Right click on VM and select settings(Or however you get there for your instance)
            Processors == 4 CPUs
            Memory  == 12 GBs RAM || 12,300MBs RAM
            (2)Network Adapters/NICs(Network Interface Cards) == 1.Used for sniffing 2.used for management of the device
            Storage/HHD/SSD == 200GBs || 200,300 MBs of storage available 
        Open advanced settings
            Pre-allocated disk can have better performance, but it takes up the full disk space at all times.
            Split into multiple files. (AKA Thin provisioning)
        Bus Type: SCSI

4. Follow the prompts to complete the installation and reboot.

5. You may need to eject the ISO image or change the boot order of the machine to boot from the newly installed OS.

FROM The SECURITY ONION splash page

1. Install Security Onion 2.3.0* (Select this option)
   Install Security Onion 2.3.0 in basic graphics mode
   Test this media & install Security Onion 2.3.0

   Troubleshooting

    Press Tab for full configuration options on menu items

2. 2nd screen from the CLI(Command Line Interface)
**W A R N I N G**
-----------------
Installing the Security Onion ISO
on this device will DESTROY ALL DATA
and partitions!
** ALL DATA WILL BE LOST **
Do you with to continue? (Type the entire word 'yes' to proceed.)
yes (press enter)

A new administrative user will be created. This user will be used for setting up and administering Security Onion.

Enter an administrative username: analyst

* NOTE: This is NOT the username for the Security Onion Console. This is the user for the underlyingn Operating System. i.e. Ubuntu || CentOS 7 in the case of this example.

Let's set a password for the analyst user:

Enter a password: ****
Re-enter the password: ****

6. Login using the username and password you set in the installer.

7. Security Onion Setup will automatically start. If for some reason you have to exit Setup and need to restart it, you can log out of your account and then log back in and it should automatically start. If that doesn’t work, you can manually run it as follows:

sudo SecurityOnion/setup/so-setup iso


AFTER THE INSTALL your final screen should say ...
Initial Install Complete. Press [Enter] to reboot!


8. Proceed to the Configuration section.

========================= EOF =========================================================================

# If you wanted to install on Ubuntu or CentOS
''
Installation on Ubuntu or CentOS
If you want to install Security Onion on CentOS 7, Ubuntu 18.04, or Ubuntu 20.04 (not using our Security Onion ISO image), follow these steps:

Review the Hardware Requirements and Release Notes sections.

Download the ISO image for your preferred flavor of 64-bit CentOS 7, Ubuntu 18.04, or Ubuntu 20.04. Verify the ISO image and then boot from it.

Follow the prompts in the installer. If you’re building a production deployment, you’ll probably want to use LVM and dedicate most of your disk space to /nsm as discussed in the Partitioning section.

Reboot into your new installation.

Login using the username and password you specified during installation.

Install prerequisites. If you’re using CentOS 7:

sudo yum -y install git
If you’re using Ubuntu 18.04 or Ubuntu 20.04:

sudo apt -y install git curl ethtool
Download our repo and start the Setup process:

git clone https://github.com/Security-Onion-Solutions/securityonion
cd securityonion
sudo bash so-setup-network
Proceed to the Configuration section.

NOTE: If any interfaces intended to be used for monitoring were automatically configured via DHCP during Ubuntu installation, setup will ask you to remove them from other network management tools. The following steps will be required to ensure the devices are managed by nmcli:

Remove monitor interface declarations from /etc/netplan/00-installer-config.yaml and then run:
sudo netplan apply
sudo touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
sudo service network-manager restart
Re-run setup.

''