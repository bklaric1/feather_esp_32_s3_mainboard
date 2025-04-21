# feather_esp_32_s3_mainboard

## Main board PCB for the second version of the first project at Technical University of Applied Science Augsburg

### Explanation
This repo contains the KiCad 8 files for the main board and the daughter board of the project.  
Necessary files are located in the source folders with the corresponding names, whilst the 3D-models, symbols and footprints can be found in the models, symbols, and footprints folders.  
The rules files are located in the source folders, and correspond with the [2 Layer HD Design Rules](https://community.aisler.net/t/2-layer-hd-design-rules/3732) from Aisler DE.  
The BOM files are located in the source folders in the *bom* folder. They are created using [Interactive HTML Bom](https://github.com/openscopeproject/InteractiveHtmlBom) Plugin. To view the BOM file, clone the repo and open them locally.  
The idea of the design is to make a battery powered system with [Adafruit ESP32-S3 Feather](https://www.adafruit.com/product/5477) as the microcontroller to control the e-paper display. We used the [7.5 inch tri-color electronic paper display](https://www.good-display.com/product/394.html) with the partial refresh as our e-paper display, but any e-paper display from [Good Display](https://www.good-display.com) and from [Waveshare](https://www.waveshare.com) would work, as there is an integrated 3.3V to 5V Boost-Converter which can be turned on if needed (per switch).  
The system is made up from two main PCBs, one that houses the microcontroller and the other which serves as a front panel Board for the buttons.  
All the parts, except the microcontroller, are sponsored by Würth Elektronik. Many thanks to them, as without them sponsoring the parts, the production of the boards would be too expensive for a student project.  
The case for the display, PCBs, and the battery pack are all designed by us and 3D printed.  

### Mainboard
The main board houses the already mentioned Adafruit ESP32-S3 Feather microcontroller. We used the version with 4 MB Flash and 2 MB PSRAM, as we needed the RAM to store a part of firmware on it (static images). The pinout is the same as some other version, so the PCB Design can be used with them as well.  
As already mentioned, there is a 3.3V to 5V Boost-Converter implemented on the board. It is found in the configuration provided by the Würth Elektronik. To switch the output voltage on the display's voltage pin, one needs to only move the switch in another position, as labeled on the board.  
The pinout for the display connector corresponds to the two display manufactures I mentioned above, but check the pinouts before connecting.  
The connector for the board is the connector that links the two boards together.  
Implementation of the external reset button isn't fully finished, but rather left as two pins on the board. I wasn't sure if we'll need to move the reset button somewhere more accessible, so I left it like that. There is no need for another reset button on the board because the microcontroller already features a built-in reset button.  
I also brought the IIC pins out on the board, in case a sensor is need later. These pins are already used internally for the battery monitoring through the MAX17048 chip.  
The battery connection is found directly on the microcontroller module. It is the JST 2-PH plug.  
The microSD adapter is designed by the specification of the espressif themselves, according to their [README](https://github.com/espressif/esp-idf/blob/master/examples/storage/sd_card/sdmmc/README.md). I also fully modified the design to make it possible to switch from the 4-wire connection (SD mode) to the 1-wire connection (SPI), in case we need more GPIO pins for something else.

### Daugtherboard
The design of the daughter board is very simple. It only includes the four buttons with the debouncing design respectively. 
The connector links with the main board to make the system complete.
Board only has one mounting hole, because of the maximum length constrains. We designed the plugin spot for the board on one side, similar to the M.2 SSD mounting technology.

### Battery Pack
As we needed to build a battery powered system, we researched and put together a battery pack with 10 600 mAh and the nominal voltage of 3.7V (4.2V) fully charged.  
The battery pack consists of two 21700 Li-Ion batteries. We have chosen [these](https://www.akkuteile.de/lithium-ionen-akkus/21700/bak/bak-n21700cd-53e-mit-5300mah-10a-3-6v-3-7v-li-ionen-akku_100625_3323) because of the high capacity and small form factor.  
Though any combination of the batteries would work, we decided to maximize the space we have in the case and the budget of our project. That is why we selected these specific cells.  
We also included the already developed [BMS](https://www.akkuteile.de/1s-pcb-keeppower-xzd-1s5530-schutzelektronik-7a_200501_1407) (Battery Management System) PCB to protect the batteries of the deep discharge, overcharge and short circuit.  
