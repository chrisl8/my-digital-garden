---
{"created":"2025-12-29","time":"Monday, December 29th, 2025 @ 2:36:51pm","tags":["unknown","dg"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/vorpal-the-hexapod/","dgPassFrontmatter":true}
---

# Links
 - [Wiki Home](https://vorpalrobotics.com/wiki/index.php/Vorpal_Robotics)
     - [Small Model Assembly Instructions](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Assembly_Instructions)
 - [Hackaday Site](https://hackaday.io/project/27260-the-vorpal-combat-hexapod)
     - This has a partial Bill of Materials that you can match up with the one on the assembly instructions
 - [Forum](https://groups.google.com/g/vorpal-robotics-forum)
 - [Dropbox Folder](https://www.dropbox.com/scl/fo/fvv6gn3padbi9jurnv2wh/AF3xURIxJu7hB-LPlI3XGLo?rlkey=06pvu3fn9n2sj2sjqha80nhr7&e=3&dl=0)
     - This appears to be the only place where one can obtain the STL files for 3D printing and the Arduino C code files.
     - I suggest just downloading the entire thing using the "Download" button on the Dropbox site. This will download a ZIP file of everything
         - Note that it will suggest that you set up an account, but that is **not** required. There should be a "Or continue with download only" link somewhere on the popup.
# What to Buy
[Wiki Bill of Materials](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Assembly_Instructions#ROBOT_BOM)
[Hackaday Component List](https://hackaday.io/project/27260/components)
The [Vorpal Store](https://vorpal-robotics-store.myshopify.com) may or may not be defunct, but it at least has good examples of what to buy.

I purchased almost everything from Amazon. I've listed many sources and searches for each part. **Look for the "Amazon Item" (and in one case "Ebay Item") links below for the exact items that I purchased though.**
(No, I am not getting any "affiliate kickbacks" for these links, they are as generic as possible. I will never know that you clicked them, and Amazon will never know that you got the links from me.)
## Parts for the Hexapod
### Electronics
- Passive Piezo Buzzer module and 3 wire cable (see image)
    - ![attachments/ffa78b37efd4785f64d198ffabfea31c_MD5.jpg](/img/user/attachments/ffa78b37efd4785f64d198ffabfea31c_MD5.jpg)
    - *Check through my parts, as I might have one.*
    - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/output/products/passive-buzzer-module)
    - ***I did not purchase one of these. I may have one or I may skip it.***
- 2 x Arduino Nano, 5V, 16 mHz, ATMEGA328 or similar
    - One for the bot and one for the controller
    - This comes in both 5V and 3.3V variants. **Be sure to get the 5V variant.**
    - DC input 3.3V up to 12V, so the controller can run directly from a 9V battery.
    - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/arduino-and-shields/products/arduino-pro-mini-atmega328-5v-16mhz-unsoldered)
    - [Adafruit](https://www.adafruit.com/product/2378) - $14
    - [Amazon Search](https://www.amazon.com/s?k=arduino+pro+mini+328)
    - **[Amazon Item](https://www.amazon.com/HiLetgo-Atmega328P-Replace-ATmega128-Atmega328/dp/B07X2JGS69/)**
        - 3 for $14
        - [[attachments/b19d564c1d25c300c361d79043049801_MD5.jpg|HiLetgo Pro Mini Atmega328P]]
![attachments/b19d564c1d25c300c361d79043049801_MD5.jpg](/img/user/attachments/b19d564c1d25c300c361d79043049801_MD5.jpg)
 
- Rotary potentiometer, 10K Ohms, 6mm shaft diameter, with 3 wires pre-soldered. Also, matching dial cap and nut.
    - **[Amazon Item](https://www.amazon.com/dp/B07B64MWRF?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_1)**
        - *Note: Unlike the rest of the parts listed, I already owned this set of potentiometers, so it was not picked specifically for this project, but it works.*
- 2 x HC05 Bluetooth Module with 4 x F-F jumper wires for making connections (Note: the HC05 has six pins but only four are used in this project.)
    - One for the bot and one for the controller
    - [Guide](https://en.hwlibre.com/Complete-guide-to-the-HC-05-and-HC-06-Bluetooth-modules-for-Arduino./)
    - [Amazon Search](https://www.amazon.com/bluetooth-module-hc05/s?k=bluetooth+module+hc05)
    - **[Amazon Item](https://www.amazon.com/dp/B07VL725T8)**
- 1 x Servo Controller module (Adafruit 16-channel 12-bit I2C PWM/Servo driver or Adafruit clone) with F-F jumper wires for making connections, plus 1 two-pin shunt tying V+ to VCC
    - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/motors-and-servos/products/16-channel-pwm-servo-driver)
    - [Adafruit](https://www.adafruit.com/product/815)
    - [Amazon Search](https://www.amazon.com/s?k=16-channel+pwm+servo+driver)
    - **[Amazon Item](https://www.amazon.com/dp/B07BRS249H)**
- 12 x MG90 micro servo motors and associated servo horns (you will only use the single-arm horn). NOTE: If your kit includes O-rings or washers, you will need to use those on the shaft of the hip servos only. These are needed for digital servos only. Many counterfeit servos claim to be digital but are really analog and don't need the washers. For more information see [Tower Pro MG90S Vs. Clones](https://vorpalrobotics.com/wiki/index.php/Tower_Pro_MG90S_Vs._Clones "Tower Pro MG90S Vs. Clones").
    - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/motors-and-servos/products/vorpal-brand-mg90-micro-servos)
    - [Amazon Search](https://www.amazon.com/tower-pro-mg90s/s?k=tower+pro+mg90s)
    - **[Amazon Item](https://www.amazon.com/dp/B0BWJ26PX2)**
        - I purchased 10 packs. You need 12 servos, so I purchased 2 of these, leaving me with 8 "spares".
- 1 x Power distribution wiring with on/off switch, Battery holder for two 18650 cells, 3A 5V BEC, and female connectors to distribute power. If you are self-sourcing see our [Circuit Diagrams](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Battery/Switch_Construction "Vorpal The Hexapod Battery/Switch Construction").
    - Switch
        - "The hole for the switch in the 3D models is 10mm x 14mm to accommodate a switch with hole profile 9mm x 13mm."
        - Note that the Vorpal information doesn't measure them quite the same way as everyone else.
        - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/products/on-off-rocker-switch-pack-of-2)
        - **[Amazon Item](https://www.amazon.com/10pcs-10x15mm-Rocker-Switch-Black/dp/B079JC8HKH/)**
    - Battery Holder for two 18650 cells
        - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/battery-and-power/products/two-cell-18650-battery-holder)
        - [Amazon Search](https://www.amazon.com/dual-18650-battery-holder/s?k=dual+18650+battery+holder)
        - **[Amazon Item](https://www.amazon.com/dp/B0BJV9ZL3J)**
    - 3A 5V BEC
        - "BEC" stands for Battery Eliminator Circuit. Originally designed to allow using the drive battery in a remote control device to run low-voltage electronics instead of requiring separate batteries.
        - This is "just" a step-down voltage regulator, but the "BEC" is a common and easy to obtain option.
        - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/battery-and-power/products/bec-5v-3a)
        - [Adafruit](https://www.adafruit.com/product/1385)
        - [Amazon Search](https://www.amazon.com/s?k=3A+5V+BEC)
        - **[Amazon Item](https://www.amazon.com/dp/B0CQ1R55BV)**
            - The instructions call for a 3A BEC, but then go on to say that some fail. I'm hoping this 5A model will be more than adequate.
    - Connectors
        - "40 pin pack of Dupont 1p-1p female jumpers"
            - These are used for making connections between Nanos, servo controllers, etc.
            - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/misc-electrical-components/products/f-f-dupont-wire-jumpers-40)
                - The store sells packs of:
                    - 10cm multi-color (40 count)
                    - 20cm multi-color (40 count)
                        - [Adafruit](https://www.adafruit.com/product/4447)
                    - 20cm black & white (10 count)
            - I ended up buying two lengths from Amazon and used both in various places:
                - **[Amazon Item](https://www.amazon.com/dp/B07GD312VG)**
                - **[Amazon Item](https://www.amazon.com/dp/B07GCY6CH7)**
- _Fasteners:_
    - For Servos
        - 12 x Socket Head Cap Screws, 2.5mm diameter by 8mm long (for servo horns) as the included screws will be too short
            - **[Amazon Item](https://www.amazon.com/dp/B0D7S1H34P)**
    - For on/off switch
        - 3 x #6-32 x 1/2" screw to fasten on/off switch adapter (2) and to hold electronics caddy on chassis (3)
        - These are button head socket cap screws
        - [[attachments/06754230c00b22506cb58f07109c33db_MD5.jpg|Open: Pasted image 20251230215114.png]]
![attachments/06754230c00b22506cb58f07109c33db_MD5.jpg](/img/user/attachments/06754230c00b22506cb58f07109c33db_MD5.jpg)
- For Accessory Port
    - *Note: I did not buy any of these so far. I play to come back to the accessory port later. For now I'm skipping it.*
        - 2 x #6-32 x 3/4" hex head screw for bottom two holes in accessory port.
        - 2 x #6-32 x 1/2" hex head screw for top two holes in the accessory port.
        - 4 x #6-32 nuts to hold screws in accessory port.
        - 2 x #6-32 wingnuts to attach accessories to accessory port.
        - [[attachments/8cfabf132cec2dd0153f1ed7a5748d30_MD5.jpg|Open: Pasted image 20251230214118.png]]
![attachments/8cfabf132cec2dd0153f1ed7a5748d30_MD5.jpg](/img/user/attachments/8cfabf132cec2dd0153f1ed7a5748d30_MD5.jpg)
 - [[attachments/59363bf1affe94a702fc145cdc0685ed_MD5.jpg|Open: Pasted image 20251230214452.png]]
![attachments/59363bf1affe94a702fc145cdc0685ed_MD5.jpg](/img/user/attachments/59363bf1affe94a702fc145cdc0685ed_MD5.jpg)
- _Optional?:_
    - *I did not buy any of these either so far.*
    - 9 x 10mm diameter pairs of hook and loop self-stick circular dots. These go on the hexapod cap (hook) and accessories like eyes and nameplates (loop).
    - 7 x 10mm diameter by 3mm thick ceramic magnet, north pole marked. These are for Capture-the-Flag and Joust accessories. (Note: Not included in Bare Bones kit).

## Parts for the Controller
Some bits were already covered above, so this only includes additional items.
- _Electronics:_
    - 9v Battery Clip
        - **[Amazon Item](https://www.amazon.com/dp/B08SL9X2YC/)**
    - 1 x 4x4 button matrix with associated connecting wires. The matrix we use is marked YL-102 in the corner. See the picture. It's blue and has the keys number K1 through K16. You may be able to use others but the pin numbers may differ.
        - ![attachments/6ae0e68361352a67b9c479e137d94cf3_MD5.png](/img/user/attachments/6ae0e68361352a67b9c479e137d94cf3_MD5.png)
        - I was not able to find this exact item anywhere at all, so I purchased this similar item from Amazon:
            - **[Amazon Item](https://www.amazon.com/dp/B07QKCQGXS/)**
                - The Gamepad Button Carrier and Cover must be modified to fit this.
    - 1 x Dpad Button module with associated connecting wires. The one we use is marked Keyes_AD_Key and has yellow buttons and a red circuit board. See picture.
        - ![attachments/335247a1239aee2026229ad40eb0f72c_MD5.png](/img/user/attachments/335247a1239aee2026229ad40eb0f72c_MD5.png)
        - I could not find these on Amazon, but I found them on Ebay, so I purchased this one item via Ebay:
            - **[Ebay Item](https://www.ebay.com/itm/383572603225)**
    - 1 x microSD Card Reader module and six wires to connect it, and a microSD card that is compatible with the Arduino SD library. A microSD card is required for record/play features to work. The capacity should be 2 gb or less, either SD or SDHC format. The gamepad can be used to format the card for use by Arduino (hold down W4 while booting the gamepad, count to 10 slowly, release W4).
        - **[Amazon Item](https://www.amazon.com/HiLetgo-Adater-Interface-Conversion-Arduino/dp/B07BJ2P6X6/)**
- _Fasteners:_
    - 4 x #6-32 x 1/2" screw to hold cover on gamepad
        - Note that you will see references to screws to hold the switch in, but the current model does not use them.
        - **[Amazon Item](https://www.amazon.com/dp/B0D2ZZVLRL)**
# Build
I followed the YouTube videos provided on the [Vorpal The Hexapod Assembly Instructions](https://www.vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Assembly_Instructions#VIDEO_BUILD_INSTRUCTIONS) page.
## 3D Printed Parts
The Controller ("Gamepad") Button Carrier and Cover would not fit the button matrix that I purchased from Amazon, so I modified them to fit.
 - [Expanded Gamepad Button Carrier](https://ekpyroticfrood.net/public-files/vorpal-hexabot/Gamepad_V1r9a_Button_Carrier_Expanded_for_Tegg_Matrix.stl)
 - [Expanded Gamepad Cover](https://ekpyroticfrood.net/public-files/vorpal-hexabot/Gamepad_V1r9a_Cover_Expanded_for_Tegg_Matrix.stl)
## Building Notes
 - Note that the video includes the old style power switch that had its own extra 3D printed part. The current design does away with that.
## Wiring
The wiring diagrams are also on the same page, but here they are again for my own reference. I had to reference the image of my board and these a lot as the pins are not in the same location.
- [[attachments/b19d564c1d25c300c361d79043049801_MD5.jpg|HiLetgo Pro Mini Atmega328P]]
![attachments/b19d564c1d25c300c361d79043049801_MD5.jpg](/img/user/attachments/b19d564c1d25c300c361d79043049801_MD5.jpg)
 
 [[attachments/4c37333aff4540361ddce4bcc0dbd4fa_MD5.jpg|Vorpal Hexapod Arduino Wiring Diagram Image]]
![attachments/4c37333aff4540361ddce4bcc0dbd4fa_MD5.jpg](/img/user/attachments/4c37333aff4540361ddce4bcc0dbd4fa_MD5.jpg)
[Vorpal Hexapod Arduino Wiring Diagram Link](https://www.vorpalrobotics.com/wiki/images/5/51/Hexapod-Nano-Diagram.JPG)
[[attachments/bcb482f130a55499e3dc593f383a3556_MD5.jpg|Vorpal Controller Arduino Wiring Diagram Image]]
![attachments/bcb482f130a55499e3dc593f383a3556_MD5.jpg](/img/user/attachments/bcb482f130a55499e3dc593f383a3556_MD5.jpg)
[Vorpal Controller Arduino Wiring Diagram Link](https://www.vorpalrobotics.com/wiki/images/8/86/Gamepad-Nano-Diagram-v3.JPG)

**Note some pin translations:**
 - VIN = RAW
 - VCC = +5V
# Software
The install is a pretty typical Arduino install.
**The one gotcha I ran into** is that it will complain that it is missing the SDFat library. **Install this from the downloaded ZIP file** using the Arduino Sketch->Include Library -> Add .ZIP library
[[attachments/5f986f6cec5304d6bf177afc6c91de88_MD5.jpg|Open: Pasted image 20260115155840.png]]
![attachments/5f986f6cec5304d6bf177afc6c91de88_MD5.jpg](/img/user/attachments/5f986f6cec5304d6bf177afc6c91de88_MD5.jpg)
If you try to use any other SdFat library, for instance one that you can get via the Arduino Library Manager:
1. It probably still won't build.
2. If you do manage to get it to build, the result may be too large for your Arduino Mini board's memory.

I did not have to modify the code in any way to get it to upload to my boards.

