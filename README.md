# Portable Cell Network

## Usage

To deploy your own portable cell network you'll need:

1. [Raspberry Pi (We used a 3rd Generation Model B Pi)](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)
2. MicroSD Card (32GB Reccommended)
3. [Nuand BladeRF (We used the BladeRF x40, the smaller card offered by Nuand)](https://www.nuand.com/blog/product/bladerf-x40/)
4. SSH enabled on the Pi (For ease of use, Terminal works fine too)
    
    Raspberry Pi Util
    ```bash
    sudo raspi_config
    > 7 Advanced Options
    >> A4 SSH
    >>> Yes
    ```

    Edit Directly
    ```bash
    mv /etc/rc2.d/ssh/K[XX]ssh /etc/rc2.d/ssh/S02ssh #XX may vary on your system, for me it was 01
    sudo systemctl enable ssh.socket
    sudo reboot
    ```
5. Fetch and configure the install script from this repository

    ```bash
    wget https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/PortableCellNetwork.sh #Download script
    chmod +x ./PortableCellNetwork.sh #Add execute functionality
    ```
6. Run script

    ```bash
    sudo ./PortableCellNetwork.sh
    ```
7. The script will walk you through customizing the cell network name and then kick off
8. After the packages are installed and configured for the BladeRF, the script will pause and ask you to connect the BladeRF to the Raspberry Pi
9. Once connected, press any key to continue and the script will detect if the BladeRF is present and continue until installation is complete

### Current Installation Time: Thu 23 Feb 18:30:53 UTC 2017 > Thu 23 Feb 18:55:08 UTC 2017 = ~25 Minutes

## Pre-built Image

Additionally, you can skip compiling above by downloading this SD card image file (in this repository) and flashing to your SD card.