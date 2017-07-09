# MMDVM_HS_Hat
MMDVM_HS Hat for the Raspberry Pi (Zero)

This project provides a Raspberry Pi Hat for the [MMDVM_HS Hotspot](https://github.com/juribeparada/MMDVM_HS). It was designed for the Raspberry Pi Zero, but should work on any other Pi with the Hat interface. 

First revisions of the board have been built successfully!

![PCB](https://github.com/mathisschmieder/MMDVM_HS_Hat/blob/master/mmdvm_hs-hat.png)

The PCB is designed in KiCad and the necessary libraries are included. The supplied Gerber files can be used to order PCBs, for example at Elecrow or DirtyPCBs. The board's dimensions are 65x30mm.

You can order 3 beautiful, purple Revision 1 PCBs at [OSHPark](https://oshpark.com/shared_projects/SfNkEo26)! 

## Revisions
### Revision 0
This was the first released version that still contains a couple of errors. There is a trace missing between L1 and C1 that needs to be fixed with a small blob of solder or magnet wire. Otherwise the RF connector is not connected to the ADF7021. The GND side of C20 and C22 is not connected to the rest of the board's GND, this needs to be fixed with a little wire to any other GND. CE is connected directly to +3.3V which disallows mode scanning to work. If you just use one mode this is fine, otherwise the connection to the CE pin has to be cut and connected to PC14 on the STM32.

Earlier schematics showed C14 as 1uF. This is wrong and needs to be replaced with 1nF, otherwise the ADF7021 will neither receive nor transmit properly.

With these changes, you can build a fully working MMDVM_HS with the old revision 0 boards

### Revision 1
These boards have "Revision 1" written on them. All bugs found in revision 0 are fixed in this version. Apart from that, the STM32's BOOT0 and RESET pins are connected to GPIOs of the Raspberry Pi. This way, flashing should be possible without manually jumpering BOOT0 and triggering a reset.

Component placement did not change between revisions 0 and 1, therefore any stencils for revision 0 should work for revision 1 boards, too.

## BOM
~~All necessary parts can be ordered at Mouser using the following [shopping cart](http://www.mouser.com/ProjectManager/ProjectDetail.aspx?AccessID=9075204188)~~

There are a couple of errors in the shopping cart. For now, don't use it, or replace the ADF7021-N with the non-N variant and replace the 0201 parts with their 0402 counterparts. Will be fixed soon!

The BOM Excel sheet is not updated to Revision 1. This will be fixed, soon, too. If you're eager to order now, extract the components and values from the schematics or the KiCad file. A current BOM would be welcome and such pull requests would surely be accepted. :)

## License
This project is released under the Creative Commons Attribution-NonCommercial-ShareAlike 3.0 (CC-BY-NC-SA 3.0, https://creativecommons.org/licenses/by-nc-sa/3.0/) license. You may edit and share it as you like, as long as credit is given and the license is not changed. You can build as many boards for you and your friends as you like and you can even sell it to them to cover your costs, **however it is strictly forbidden to turn this into a commercial product! You are not allowed to build and sell these boards for profit!**
