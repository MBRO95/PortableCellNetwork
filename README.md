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
8. After the packages are installed and configured for the BladeRF, the script will detect if the device is present and, if not, it will pause and ask you to connect the BladeRF to the Raspberry Pi. Once connected, press any key to continue and the script will continue until installation is complete.
9. Reboot the Pi
    ```bash
    sudo reboot now
    ```
10. Run the 'StartYateBTS.sh' script located in the home directory
    ```bash
    sudo ./StartYateBTS.sh -i #It's important to keep the '-i' flag so the script runs interactively
    ```

#### Current Installation Time: Tue 21 Mar 13:15:08 UTC 2017 > Tue 21 Mar 14:16:37 UTC 2017 = ~61 Minutes

## Pre-built Image

Additionally, you can skip compiling above by [downloading this SD card image file](https://1drv.ms/u/s!AgREYOhKnDOGnPUc4JhPeDZXMcWJjw) and flashing to your SD card.