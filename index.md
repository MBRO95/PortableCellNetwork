---
layout: default
---
# Project Documentation
### Project By: Matthew May & Brendan Harlow for Champlain College SEC-440

# Introduction

The goal of this project is to create a private secure portable cell network utilizing basic technologies for mobile phones that can be easily deployable in any situation. In the event of an emergency, commodity cell networks can easily become severely congested and overwhelmed. Having the ability to set up secure and reliable communications for civilians or law enforcement can save lives, facilitate responses, and provide confidence in decision making.

The radio system that we are using for the cell phones to communicate with is the GSM protocol (Global System for Mobiles) more commonly used by cellular provider such as AT&T and T-Mobile. To broadcast the radio system, we are going to be using a Software Defined Radio (SDR) device called the BladeRF (external). This hardware is controlled by the Raspberry PI (small single-board computer) (external) using YateBTS (external) which is software that implements functions and protocols of both the radio access network and the core GSM network to allow cell phones to communicate using voice, text, and data. The Raspberry PI is instrumental to reach our goals of portability due to its size, low power usability, and cost over alternatives.  

# Prerequisites

### To deploy the portable cell network using our instructions you'll need the following:
- Raspberry Pi (We used a 3rd Generation Model B Pi)
- MicroSD Card (32GB Recommended)
- Nuand BladeRF (We used the BladeRF x40, the smaller card offered by Nuand)
- SSH enabled on the Pi (For ease of use, Terminal works fine too)
- GSM and SIM card compatible phones
- SIM cards (sysmoSIM-GR2)
- Ethernet Cable (If you desire the phone's to have local internet connectivity)

# Raspberry Pi Setup
[**Click here for a photo-rich version of these instructions**](PiPhotoGuide).
- Plug-in the Ethernet, Power Supply, and Keyboard to the Pi and then plug the power adapter into the wall. When you reach the login screen login with the default credentials
  - Username: pi
  - Password: raspberry
- Run

```bash
sudo raspi-config
```

## Change Keyboard Layout
- Scroll down to ‘Localisation Options’ and press ‘Enter’
- Scroll down to ‘Change Keyboard Layout’ and press ‘Enter’
- Scroll down to ‘Other’ and press ‘Enter’
- Scroll down to ‘English (US)’ and press ‘Enter’
- Scroll to the very top to ‘English (US)’ and press ‘Enter’
- Hit ‘Enter’ to accept the defaults on the next two screens, since they don't apply.
- When you get past the last two steps you will be returned back to the main menu.

## Enable SSH
- Scroll down to ‘Interfacing Options’ and press ‘Enter’
- Scroll down to ‘SSH’ and press ‘Enter’
- Scroll to ‘Yes’ and press ‘Enter.’
- On the next screen, press ‘Enter’ to go back to the main menu.
- When you've reached the main menu, scroll to the right and select ‘Finish,’ then press ‘Enter'
- When back at the terminal, run the command below to enable the configured settings.

```bash
sudo reboot now
```

# Network Deployment
To make your life easier, SSH to your Raspberry Pi.
Note your Pi's IPv4 address from the command below:

```bash
ifconfig eth0
```

On another computer, utilize a terminal application and run: 

```bash
ssh pi@[INSERT PI IPV4 ADDRESS HERE]
```

- Once prompted for credentials, again, enter:
  - Username: pi
  - Password: raspberry

### Now we are interacting with the Pi remotely.
### Let’s start gathering what we need for deployment.

```bash
# Download the script from GitHub
wget https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/PortableCellNetwork.sh

# Make the downloaded script executable 
chmod +x ./PortableCellNetwork.sh
```

### The script will check to make sure you’re running as root, so make sure you don't leave out the ‘sudo’ portion of the commands below.

#### To run the script without logging its output, issue:

```bash
sudo ./PortableCellNetwork.sh
```
#### To run the script while logging its output, issue:

```bash
sudo ./PortableCellNetwork.sh | tee install.log
```

- The script will query you for a network name
  - Provide one and confirm it
  - OR 
  - press ‘Enter’ to accept the default name of ‘DuaneDunstonRF’
- Confirm your network name
- The script will now initiate the installation and configuration process. This will take close to an hour so you can go find something to do in the meantime.
- When the script is nearing completion it will query for a new user password for the ‘pi’ user.
  - Enter and re-enter this password to change from the default for added security.

### When the script completes it will report how much time it took to run and wait for a keypress to reboot.
- Press any key to reboot the pi.
  - You will be rebooted into a desktop environment, simply select the ‘Default Configuration’ option at the pop-up that launches at first boot.
- A startup script titled ‘StartYateBTS.sh’ will await you in ‘/home/pi’ and will start the cell network processes. 
  - To boot the startup script it is imperative that it is run in interactive mode by passing the ‘-i’ flag after the script name, like below:

```bash
sudo ./StartYateBTS.sh -i
```

### Once started, this script will:
- Open a terminal window reporting the Yate (cell network) status
- Open a Firefox browser window that will navigate to YateBTS (web-based cell network configuration)
  - Here you can view/modify network configuration settings and manage/write SIM cards for devices.

# Phone Deployment
To join a compatible phone to the cell network, SIM cards need to be deployed to work with the correct settings. YateBTS uses a utility called PySIM, a python tool for programming SIM cards. In the installation script PySIM is already set up as the correct version that supports the SysmoSIM-GR2 card type. To start, make sure that the compatible SIM card writer is inserted into the Raspberry Pi with the SIM card to program already in it. 

Open the tab called Manage SIMs as shown below and make sure that the Generate random IMSI setting is checked and the Insert subscribers is unchecked. The insert subscribers setting will break the functionality of the cell network and is recommended to avoid unless there is a fix for it. 
![Image of SIMprogramming1](https://github.com/MBRO95/PortableCellNetwork/blob/master/Pi%20Startup/SIMprogramming.png)

The next step is to check that the correct settings have been set in the Advanced drop down bar. Make sure the Operator name reflects the correct setting that was chosen for the cell network. Otherwise use the default settings and hit save. 
![Image of SIMprogramming2](https://github.com/MBRO95/PortableCellNetwork/blob/master/Pi%20Startup/SIMprogramming1.png)

The screenshot below shows an example output that the SIM programming was successful. And lastly that the deployed SIM card shows in the Manage SIMs list. 
![Image of SIMprogramming3](https://github.com/MBRO95/PortableCellNetwork/blob/master/Pi%20Startup/SIMprogramming3.png)

After inserting the SIM card into the GSM phone and powering on, YateBTS will send a welcome message with the assigned number for the phone as shown in the screenshot below. To troubleshoot if the Android phone is not connecting to the cell network properly, open the dialer application and type: 
*#*#4636#*#*
A menu will appear and in the phone information tab, select the preferred network type to be GSM only and restart the phone.
![Image of SIMprogramming4](https://github.com/MBRO95/PortableCellNetwork/blob/master/Pi%20Startup/phone.jpg)

# Security Overview
A security model was implemented in our installation script based on the Center for Internet Security (CIS), which is a highly reputable source for best practice information security. The script incorporates a benchmark model designed for Debian 8 operating system. The Debian 8 operating system is the closest relating Linux distribution to the Raspberry Pi image, therefore we decided that this model was the best choice to use for reference. Originally, we did run into a set back with the security functionality of the Raspberry Pi because it does not support custom partitions that can implement security controls, such as full disk encryption and partition modifiers that deny arbitrary executions and protect against attacks that fill up disk space. The goal of the security script was to implement as many controls as we could while keeping the functionality of the Raspberry Pi operating system and the Yate software. 

The model follows the practice of disabling anything that is unnecessary to the functionality of the system to reduce the potential attack surface. Performing periodically updates and patches to fix security flaws can be a challenge for a system that is designed to be mobile and in areas where there may not even be access to the Internet.
