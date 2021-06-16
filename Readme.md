Terminator Arm Automated Lighting

This remix/mod of the "DIY Life-Size Terminator Arm Lamp" will allow you to use individual LEDs as well as control the brightness wirelessly via Home Assistant (via ESPHome integration).  Although the included code is for Home Assistant, you can easily use the exact same hardware setup and control via Blynk, a web page, or other interfaces.

The steps below are to light the base and a top lid (which I prefer.)  If you only wish to light via the base, just exclude the top parts & its 12 LEDs - everything else is the same.



## What You'll Need ##

**Hardware**

- x1 12V DC Power Supply
- x1 LM2596 Buck Converter [(Amazon)](https://www.amazon.com/gp/product/B06XZ1DKF2/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
- x1 IRF520 MOSFET Driver [(Amazon)](https://www.amazon.com/gp/product/B01I1J14MO/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
- x24 3V/20ma White LEDs [(Amazon)](https://www.amazon.com/gp/product/B01AKPKC84/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
- x1 Wemos D1 Mini [(Amazon)](https://www.amazon.com/gp/product/B08MKLRSNH/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1) or NodeMCU [(Amazon)](https://www.amazon.com/HiLetgo-Internet-Development-Wireless-Micropython/dp/B081CSJV2V/ref=sr_1_3?dchild=1&keywords=nodemcu&qid=1623877448&s=electronics&sr=1-3)
- x1 Pair DC Power Pigtail Cable [(Amazon)](https://www.amazon.com/gp/product/B072BXB2Y8/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
- Wire - I used 24AWG [(Amazon)](https://www.amazon.com/gp/product/B07V1D82HM/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)

**Tools**

- 3D Printer (or the parts printed)
- Soldering iron + Solder
- Multimeter
- Wire stripper
- Heat Shrink tubes

**Notes**

- The parts linked above are what I personally used - others may work too.
- If you use LEDs which are not exactly rated to be 3V each, you must add resistors.  Use a resistor calculator to find out which to use. 

## Steps ##

**Configure Microcontroller for Home Assistant / ESPHome**

1. Add the ESPHome integration to Home Assistant 
2. Add a new Node - name and configure as needed for your microcontroller
3. Once done, edit it and paste in the posted code - make sure to change your SSID / password and anything else as needed
4. Save the code, then compile and download the BIN file
5. Connect the microcontroller to the PC via USB then use [ESPHome-Flasher](https://github.com/esphome/esphome-flasher) to flash the BIN to it


**Assemble Top**

1. If including the top lighting, print the two STLs included.  I used PLA with a 10% infill, and 0.6mm nozzle.  Optionally sand, prime, and paint once done
2. Attach male end of DC Power Pigtail Cable to end of 12V DC Power Supply.
3. Using a touch of glue, insert an LED into each of the holes in the Top Mount *(You may have to drill holes a bit to make them fit)*
4. Wire the x12 LEDs as shown in the lower left of the diagram which should result in x3 sets of x4 LEDs wired in series.  Each of the x3 sets should then be wired in parallel with the pair of wires being long enough to reach the stand's base.

**Assemble Base**

***Important:**  Before hooking everything up, connect 12V to the inputs of the buck converter, a multimeter to the output, and turn the screw until it yields ~5.25V.*

5. Wire the LEDs for the base in the same manner, then join their pair of wires to the pair coming from the top
6. Follow the diagram to hook up all electronics.  *(I didn't use a breadboard but included it in image for demonstration purposes)*
7. The female end of the DC Power Pigtail Cable should virtually be attached to the 12V rail

Once done, plug it in and wait a few seconds for everything to load.  It may not light up initially.  In the ESPHome node of Home Assistant, the node you added should turn green once online.  Add a "Light" button to your Lovelace dashboard and configure for your device.  Add any automations desired - enjoy! 