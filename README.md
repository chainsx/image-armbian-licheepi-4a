# image-armbian-licheepi-4a

Use [Armbian official code repository](https://github.com/armbian/build)

### Download u-boot

1. Go to the [thead-u-boot](https://github.com/chainsx/thead-u-boot/actions) to download the u-boot file suitable for LicheePi 4A.

### Flashing u-boot to EMMC

Hold down the `BOOT` key and connect the power supply to the development board.

```
sudo ./fastboot flash ram ./images/u-boot-with-spl.bin
sudo ./fastboot reboot
sleep 10
sudo ./fastboot flash uboot ./images/u-boot-with-spl.bin
```

*Note that the u-boot provided by this project will not modify the partition table.*

### Flash System

1.  Flashing System to SD Card

    I don't need to tell you this, right?

    :)

2.  Flashing System to EMMC

    1)  UMS (USB Mass Storage) function using u-boot (experimental):
   
        If there is a dial switch, please set it to EMMC mode.
    
        Use the serial port to interrupt with `Ctrl^C` when counting down the seconds in u-boot to enter the u-boot command line, and then enter the following command:
        ```
        ums 0 emmc 0
        ```
        Then EMMC will map the USB Mass Storage device onto the computer.
    
    2)  After booting using the SD card, `dd` the image to EMMC.

### u-boot System Selection Order

SD card takes priority over EMMC.
