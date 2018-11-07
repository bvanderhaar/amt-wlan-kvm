# Setting up AMT with KVM over WLAN
WARNING: depending on your specific configuration this could be an insecure setup.

## Install Management Engine driver on the host
* This requires the Local Management Service (LMS)
* Download [Management Engine Driver](https://downloadcenter.intel.com/download/28083/Intel-Management-Engine-Driver-for-Windows-7-8-1-and-Windows-10?v=t) and install
  * Some systems may require OE-specific ME drivers
  * Make sure the Local Management System (LMS) is installed and running

## Run Setup and Configuration Software on the host as administrator
* Download [Setup and Configuration Software](https://downloadcenter.intel.com/download/26505/Intel-Setup-and-Configuration-Software-Intel-SCS-)
* .NET Framework 2.0/3.5 may need to be installed
* Run ACU_Wizard/ACU_Wizard.exe as administrator
* Configure/Unconfigure this system
* Configure Via Windows
* Enter the current MEBx password in the current password box
* Click Edit Configuration
* Click optional settings
* Select Home Domains, Network Configuration and Wifi Connection
* Click next and add the home domain suffixes needed to remotely access the machine
* Check the allow AMT functionality over VPN if necessary
* Select "Allow WiFi Connection without WiFi setup"
* Accept the defaults on the System Settings page
* Click Next, Finish, Next
* Set a password to encrypt the profile, click Configure

## Set KVM without user consent from AMT SDK's KVMControlApplication
* This only needs to be installed on a single computer with network access to the target machine(s) you wish to configure
* [AMT SDK Download](https://software.intel.com/en-us/amt-sdk/download)
* Install the [Visual C 2013 Redistributable](https://support.microsoft.com/en-us/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)
  * Scroll down to the x86 version (x86 bins are linked by default, x64 are available but not necessary to run the app)
* Run KVMControlApplication and configure unattended KVM as outlined in [this article](https://www.virten.net/2018/05/7th-gen-nuc-remote-management-with-kvm-using-vpro-amt/)
* Use the WiFi IP to configure KVM

## Glossary
* AMT - Active Management Technology
* MEBx - Management Engine BIOS Extensions
  * In AMT world this password is different than the RFB password
* RFB - Remote Framebuffer (related to VNC)
  * AMT requires a different RFB password chopped to 8 characters
* ME - Management Engine.  Some drivers are platform-specific
