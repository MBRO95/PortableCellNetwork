---
layout: default
---
# Raspberry Pi Setup Photo Guide
[**Click here to go back to the main documentation**](index).
- Plug-in the Ethernet, Power Supply, and Keyboard to the Pi and then plug the power adapter into the wall. When you reach the login screen login with the default credentials
  - Username: pi
  - Password: raspberry
![Login Screen](Pi%20Startup/1.jpg "Login Screen")

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
