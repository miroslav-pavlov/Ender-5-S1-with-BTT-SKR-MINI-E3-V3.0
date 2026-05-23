# Creality Ender-5 S1 with BIGTREETECH SKR MINI E3 V3.0 board
<img width="306" height="408" alt="20260523_224820" src="https://github.com/user-attachments/assets/a4a3cd08-6944-4229-92f7-50923e14d470" />  

This is an old project I did after frying the original board and not finding an exact replacement. It's beautiful, isn't it?  

---
> [!WARNING]  
> - The SKR MINI E3 board as well as all other BTT boards don't support the proprietary printer screeen and therefore need an RPi or another single-board computter capable of running klipper for an online connection.
> - I did this project a couple of months ago and don't remember everything. I fact-checked all information again, but you should still take this guide with a grain of salt.

> [!NOTE]  
> - I compiled the needed pinouts into a spreadsheet which you can find in the files of this guide.
> - I used [this YouTube video](https://www.youtube.com/watch?v=VxCBDyvFSgA) for the pinout and advise you to double check guide's information with it.
> - I used [this pinout for the BTT board](https://github.com/bigtreetech/BIGTREETECH-SKR-mini-E3/blob/master/hardware/BTT%20SKR%20MINI%20E3%20V3.0/Hardware/BTT%20E3%20SKR%20MINI%20V3.0_PIN.pdf)
> - The printer head's board is the small black board nested behind the printer head where the other side of the big ribbon cable connects. It is mentioned multiple times in this guide.
---
## Materials needed
- [JST XH-2.54 pin connectors](https://www.aliexpress.com/item/1005008791163858.html)
- [A crimping tool](https://www.aliexpress.com/item/1005008645314178.html)
- A multimeter for verifying connections
- RPi or another single-board computer for Klipper
---
## 1. Connecting the 30-Pin Cable
> [!NOTE]
> - The big ribbon cable connects to a single 30-pin port on the original board but branches into 2 cables (24-pin and 6-pin). They are mapped next to each other in the spreadsheet
> - You can find the orientation of your ribbon cable based on the white wire which is used for grounding and is also colored white in the spreadsheet.
> - The BL Touch colour table is for cross-referencing with wiring tutorials for the BL Touch as the Ender-5 S1 one has all black cables.
> - The numbering of the motors and bl touch pins (E1-E4, Y1-Y4, X1-X4 and BL1-BL5) is based on their location on the printer and is for easier verification of connections.
> - Use a multimeter to check if you did everything correct.
### Steps
1. Cut the board end of the ribbon cable and remove a part of the plastic shielding.  
2. Use the spreadsheet to crimp the cables with new connectors, then connect them to these ports:
- The **E-Motor** connects to port **EM**.
- The **BL Touch** connects to **Z-PROBE**. Consult a guide for its pinout and reference the wire colours table. I don't remember what I did here, but if I was able to do it then it's clearly possible.
- The **thermistor** connects to port **TH0**. It has no polarity and can be connected both ways.
- The **hotend** and **part-cooling** fans are **FAN1** and **FAN2**. Use the fans table to map them to the board. They are named after the white ribbons with printed text on the printer head and from the inscriptions on the printer head's board. They share a common 24V wire so one of the fan connectors can have only 1 wire (Control) because it will get its power from the the other one at the printer head's board.
- The **heat** connects to **E0**. It also has no polarity. All its right cables should be crimped together and all left ones also together. (Left and right should not be crimped together!)
- The **X-Stop** connects to **X-Stop**. It has no polarity.
- The **X-Motor** connects to port **XM**
## 2. Connecting the Y-Stop and Y-Motor
1. Cut the board end of the ribbon cable and remove a part of the plastic shielding.  
2. Use the spreadsheet to crimp the cables with new connectors, then connect them to these ports:
- The **Y-Stop** connects to **Y-Stop**. It has no polarity.
- The **Y-Motor** connects to port **YM**.
## 3. Connecting the Z-Motor
1. Cut the board end of the ribbon cable and remove a part of the plastic shielding.  
2. Crimp the cables exactly like positioned on the ribbon. No need to switch their places.  
3. Connect the **Z-Motor** to port **ZAM**. You can also use port ZBM but may need to edit the printer config.
## 4. Connecting the fillament runout sensor
Try using [this reddit port](https://www.reddit.com/r/Ender3S1/comments/1685mug/ender_creality_filament_sensor_pinout/) to connect the sensor. If it doesn't work try switching the signal and voltage :)
## 5. Connecting the bed
1. Remove a part of the plastic shielding.  
2. Connect the **chunky cables** to port **HB** with red being + and black being -  
3. Connect the **thin cables** to port **THB**. They have no polarity.
## 6. Connecting the power
1. You'll need to remove a couple of the windings from the ferrite core for the cable to reach the port. I was left with only 2 winding for the cable length to be sufficient.  
2. Connect the **power** to **POWER** with red being + and black being -
## 7. Flashing the board with Klipper
1. Follow [this guide](https://github.com/bigtreetech/BIGTREETECH-SKR-mini-E3/tree/master/firmware/V3.0/Klipper) on flashing Klipper. Both USB and UART can work. I personally chose USB.
## 8. Installing klipper on the RPi. 
1. Install klipper in the RPi. If you've never done this before, the best way is using [KIAUH](https://github.com/dw-0/kiauh). That's what I personally use.
2. Use the **printer.cfg** from this guide's files as it has the right mappings for a BTT board inside an Ender-5 S1. You can also find all of my config files uploaded to this guide in case you find them useful.
## 9. Mounting the RPi
1. You can use the mount from the description of [this YouTube video](https://www.youtube.com/watch?v=VSVQrhhNqhA).
2. Funnel all RPi cables through the cable hole on the back of the printer.
3. Optionally you can buy [this screen](https://www.aliexpress.com/item/1005008082461104.html) for [KlipperScreen](https://klipperscreen.readthedocs.io). It fits in the mount from the video and has my recommendations.
# 10. 3D Printing a mount for the board
1. Because the holes of the BTT board don't match the original one, I made a 3D printable mount which screws in the place of the old board. If you've fried the old board like me, you can leave the new one floating until the mount has been printed.
2. Use the picture from the start of the guide to correctly mount the board. You'll need a couple of small bolts and nuts or 3D print a couple of shafts to keep the board in place.
## 11. Connecting the board fan  
Connect the **board fan** to port **FAN2** without changing the connector.

You can finally close the back. Thanks for reading this guide. If you feel like I've helped you, you can leave a star :)
