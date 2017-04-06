---
layout: default
---
# Raspberry Pi Setup Photo Guide
[**Click here to go back to the main documentation**](index).
1. Plug-in the Ethernet, Power Supply, and Keyboard to the Pi and then plug the power adapter into the wall. When you reach the login screen login with the default credentials
  * Username: pi
  * Password: raspberry
2. Run ‘sudo raspi-config’
![sudo raspi-config](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/1.JPG "sudo raspi-config")
## Change Keyboard Layout
3. Scroll down to ‘Localisation Options’ and press ‘Enter’
![Localisation Options](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/2.JPG "Localisation Options")
4. Scroll down to ‘Change Keyboard Layout’ and press ‘Enter’
![Change Keyboard Layout](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/3.JPG "Change Keyboard Layout")
5. Scroll down to ‘Other’ and press ‘Enter’
![Other](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/4.JPG "Other")
6. Scroll down to ‘English (US)’ and press ‘Enter’
![English (US)](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/5.JPG "English (US)")
7. Scroll to the very top to ‘English (US)’ and press ‘Enter’
![English (US)](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/6.JPG "English (US)")
8. Hit ‘Enter’ to accept the defaults on the next two screens, since they don't apply.
![Skip 1](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/7.JPG "Skip 1")
![Skip 2](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/8.JPG "Skip 2")
9. When you get past the last two steps you will be returned back to the main menu.

## Enable SSH
1. Scroll down to ‘Interfacing Options’ and press ‘Enter’
![Interfacing Options](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/9.JPG "Interfacing Options")
2. Scroll down to ‘SSH’ and press ‘Enter’
![SSH](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/10.JPG "SSH")
3. Scroll to ‘Yes’ and press ‘Enter.’
![Yes](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/11.JPG "Yes")
4. On the next screen, press ‘Enter’ to go back to the main menu.
![Enter](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/12.JPG "Enter")
5. When you've reached the main menu, scroll to the right and select ‘Finish,’ then press ‘Enter'
![Finish/Enter](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/13.JPG "Finish/Enter")
6. When back at the terminal, run 'sudo reboot now' to enable the configured settings.
![Reboot](https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/Pi%20Startup/14.JPG "Reboot")

[**Click here to go back to the main documentation**](index).