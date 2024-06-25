![Edgeberry banner](documentation/Edgeberry_banner.png)

<img src="documentation/Edgeberry_rendering.png" align="right" width="50%"/>

The **Edgeberry Hardware** project is a Raspberry Pi compatible 'hat' providing several basics for easily using your Raspberry Pi as an IoT Edge device and deploying it in a real-world environment. Some key features are a powerful 3A step-down convertor for powering your device reliably using a regular 12V adaptor, indicators for providing status feedback, and an expansion slot for integrating application-specific hardware using an [Edgeberry Hardware Cartridge](https://github.com/SpuQ/Edgeberry-cartridge-console-can). The Edgeberry Hardware is designed to snugly fit in the [Edgeberry Enclosure](https://www.thingiverse.com/thing:6595172).

<br clear="right"/>

## Device Assembly
After acquiring (or milling and soldering) the Edgeberry Hardware, and 3D printing the Edgeberry enclosure, you're ready to assemble your device.

<p float="left">
  <img src="documentation/Edgeberry_assembly_1.png" width="32%" />
  <img src="documentation/Edgeberry_assembly_2.png" width="32%" />
  <img src="documentation/Edgeberry_assembly_3.png" width="32%" />
</p>
<p float="left">
</p>
<p float="left">
  <img src="documentation/Edgeberry_assembly_4.png" width="32%" />
  <img src="documentation/Edgeberry_assembly_5.png" width="32%" />
  <img src="documentation/Edgeberry_assembly_6.png" width="32%" />
</p>

## Edgeberry Software
On your device, install the [Edgeberry application software](https://github.com/SpuQ/EdgeBerry/) by downloading and executing the installation script
```
wget -O install.sh https://github.com/SpuQ/EdgeBerry/releases/download/v2.4.0/install.sh
chmod +x ./install.sh
sudo ./install.sh
```
If everything was successful, you can now access your Edgeberry's web interface in your local network
```
http://<device_ip_address>:3000
```
## (re)Writing the EEPROM
>[!important]
>**When you purchased the Edgeberry Hardware, the manufacturer has written the EEPROM**. If you are the manufacturer, or you're hacking your Edgeberry board, then continue with the following steps.

1) Close the `write protection` jumper (JP1) on the Edgeberry Hardware to enable writing the EEPROM
2) Download and build the [Raspberry Pi Hat eeprom utils](https://github.com/raspberrypi/hats) on your device 
3) Make the EEPROM file from the eeprom_settings.txt using `eepmake` <br> e.g. `$ eepmake eeprom_settings.txt edgeberry.eep`
4) Flash the EEPROM using `eepflash.sh` <br> e.g. `$ sudo ./eepflash -w -t=24c256 -f=edgeberry.eep`
5) Now `reboot` the device and check the device tree for your hat's settings <br> e.g. `$ cat /proc/device-tree/hat/vendor`)

## License & Collaboration
**Copyright© 2024 Sanne 'SpuQ' Santens**. This project is released under the [**CERN OHL-W**](./LICENSE.txt) license.<br/>
The [Rules & Guidelines](https://github.com/Edgeberry/.github/blob/main/brand/Edgeberry_Trademark_Rules_and_Guidelines.md) apply to the usage of the Edgeberry™ brand.

### Collaboration

If you'd like to contribute to this project, please follow these guidelines:
1. Fork the repository and create your branch from `main`.
2. Make your changes and ensure they adhere to the project's design style and conventions.
3. Test your changes thoroughly.
4. Ensure your commits are descriptive and well-documented.
5. Open a pull request, describing the changes you've made and the problem or feature they address.