# feather_esp_32_s3_mainboard

## Mainboard PCB for the second version of the first project at Technical University of Applied Science Augsburg

### Intro
This repo contains the KiCad 8 files for the Main Board and the Daughter Board of the project.
Necessary files are located in the source folders with the corresponding names, whilst the 3D-models, symbols and footprints can be found in the models, symbols, and footprints folders.
The rules files are located in the source folders, and correspond with the [2 Layer HD Design Rules](https://community.aisler.net/t/2-layer-hd-design-rules/3732) from Aisler DE.
The BOM files are located in the source folders in the *bom* folder. They are created using [Interactive HTML Bom](https://github.com/openscopeproject/InteractiveHtmlBom) Plugin. To view the BOM file, clone the repo and open them locally.

### Explanation
The idea of the design is to make a battery powered system with [Adafruit ESP32-S3 Feather](https://www.adafruit.com/product/5477) as the microcontroller to controll the e-paper display. We used the [7.5 inch tri-color electronic paper display](https://www.good-display.com/product/394.html) with the partial refresh as our e-paper display, but any e-paper display from [Good Display](https://www.good-display.com) and from [Waveshare](https://www.waveshare.com) would work, as there is an integrated 3.3V to 5V Boost-Converter which can be turned on if needed (per switch).
