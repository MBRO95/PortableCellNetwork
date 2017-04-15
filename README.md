# Portable Cell Network

To deploy your own portable cell network you can:
## Compile From Source Utilizing The Install Script
1. Fetch and configure the install script from this repository

    ```bash
    wget https://raw.githubusercontent.com/MBRO95/PortableCellNetwork/master/PortableCellNetwork.sh #Download script
    chmod +x ./PortableCellNetwork.sh #Add execute functionality
    ```

2. Run script

    ```bash
    sudo ./PortableCellNetwork.sh
    ```

3. The script will walk you through customizing the cell network name and then kick off
4. After the packages are installed and configured for the BladeRF, the script will detect if the device is present and, if not, it will pause and ask you to connect the BladeRF to the Raspberry Pi. Once connected, press any key to continue and the script will continue until installation is complete.
5. Reboot the Pi

    ```bash
    sudo reboot now
    ```

6. Run the 'StartYateBTS.sh' script located in the home directory

    ```bash
    sudo ./StartYateBTS.sh -i #It's important to keep the '-i' flag so the script runs interactively
    ```

#### Current Installation Time: Tue 21 Mar 13:15:08 UTC 2017 > Tue 21 Mar 14:16:37 UTC 2017 = ~61 Minutes

## Flash A Pre-built Image To An SD Card
Additionally, you can skip compiling above by downloading an SD card image file below and flashing to your SD card:
- [**3.21.2017 Build**](https://1drv.ms/u/s!AgREYOhKnDOGnPUc4JhPeDZXMcWJjw)
- [**3.23.2017 Build**](https://1drv.ms/u/s!AgREYOhKnDOGnPUu_dNfI7X_ntERpA)
- [**4.13.2017 Build**](https://1drv.ms/u/s!AgREYOhKnDOGnYxWUsNzRi3RbP8-rw)

For More Details, [View The Documentation Here](https://mbro95.github.io/PortableCellNetwork/).