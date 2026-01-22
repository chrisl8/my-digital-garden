---
{"created":"2025-12-29","time":"Monday, December 29th, 2025 @ 2:36:51pm","tags":["unknown","dg"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/vorpal-the-hexapod/","dgPassFrontmatter":true}
---

I've built a few [robot type things](https://www.youtube.com/@christenlofland) in the past and was itching to do some more tinkering with another home-built mechanical thing.
I wanted something small and I wanted to move away from wheels and try something with legs. I wanted something that was both fully able to be home-built and also "ready to go" once built so that I could start from something that "works already" and modify it, rather than having to start from scratch.

I found the [Vorpal Robotics](https://vorpalrobotics.com/wiki/index.php/Vorpal_Robotics) [Hexapod](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod) online and after evaluating a bunch of other multi-legged do-it-self robotic projects I was convinced that this was the best one for me.

It is one of the only options that is fully built from 3D printed parts that we can download and modify ourselves, rather than relying on vendor manufactured products.

The [Vorpal Store](https://vorpal-robotics-store.myshopify.com) sells kits (or did, I cannot tell if they are still operating?), but I wanted to do this entirely from "scratch" using parts that I sourced myself so that I could repeat the process in the future and so that I would have the understanding of the setup to modify it.

Be aware that if you follow "my way" a **significant amount of soldering will be required**. I enjoy soldering personally, but if you don't know how, this will require learning. That said, none of the soldering required is "fancy" so if you want to [learn to solder](https://learn.sparkfun.com/tutorials/how-to-solder-through-hole-soldering), this is a good first project, although if you aren't careful you could fry some cheap boards, although I've literally never done that in all of my life.

# My Results
[Here is a YouTube video of my build](https://youtu.be/Ds7JhmUr4vI?si=HqQSw6Ozl4uPzn09)
# Links
 - [Wiki Home](https://vorpalrobotics.com/wiki/index.php/Vorpal_Robotics)
     - [Small Model Assembly Instructions](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Assembly_Instructions)
     - [Vorpal Hexapod Source Files](https://vorpalrobotics.com/wiki/index.php?title=Vorpal_Hexapod_Source_Files)
         - This page explains where to get the STL and source code files.
         - [Dropbox Folder](https://www.dropbox.com/scl/fo/fvv6gn3padbi9jurnv2wh/AF3xURIxJu7hB-LPlI3XGLo?rlkey=06pvu3fn9n2sj2sjqha80nhr7&e=3&dl=0)
             - This appears to be the only place where one can obtain the STL files for 3D printing and the Arduino C code files.
             - I suggest just downloading the entire thing using the "Download" button on the Dropbox site. This will download a ZIP file of everything
             - Note that Dropbox will suggest that you set up an account, but that is **not** required. There should be a "Or continue with download only" link somewhere on the popup.
 - [Hackaday Site](https://hackaday.io/project/27260-the-vorpal-combat-hexapod)
     - This has a partial Bill of Materials that you can match up with the one on the assembly instructions
 - [Forum](https://groups.google.com/g/vorpal-robotics-forum)
# What to Buy and Where to Buy
[Wiki Bill of Materials](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Assembly_Instructions#ROBOT_BOM)
[Hackaday Component List](https://hackaday.io/project/27260/components)
The [Vorpal Store](https://vorpal-robotics-store.myshopify.com) 

I wasn't entirely sure if the [Vorpal Store](https://vorpal-robotics-store.myshopify.com) was still functioning at the time I started this project. I used it as a reference, but purchased parts elsewhere. If you can get parts from the [Vorpal Store](https://vorpal-robotics-store.myshopify.com) though, supporting them would be a good thing to do I think.

I purchased almost everything from Amazon. I've listed many sources and searches for each part. **Look for the "Amazon Item" (and in one case "eBay Item") links below for the exact items that I purchased** if you want to replicate my results or just want to spend less time researching every part.
(I am **not** getting any "affiliate kickbacks" for these links, they are as generic as possible. I will never know that you clicked them, and Amazon will never know that you got the links from me.)

I don't know who/what "HiLetgo" is, but a lot of the parts I found on Amazon for a good price with good reviews were from them, and so given the choice, I picked additional parts from them when the choice wasn't clear otherwise. That is why you will see a lot of them here. I don't have any reason to believe that they are better or worse than any others.

I did find some places on eBay that had all of these parts for good prices, but their shipping often doubled the price. I think eBay would be a good way to go though if you don't want to or cannot use Amazon. [This eBay vendor](https://www.ebay.com/str/survy2014) had an amazing array of parts. I ordered one bit from them which arrived quickly for whatever that is worth.
## Parts for the Hexapod
### Electronics
- Passive Piezo Buzzer module and 3 wire cable (see image)
    - ![attachments/ffa78b37efd4785f64d198ffabfea31c_MD5.jpg](/img/user/attachments/ffa78b37efd4785f64d198ffabfea31c_MD5.jpg)
    - *Check through my parts, as I might have one.*
    - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/output/products/passive-buzzer-module)
    - ***I did not purchase one of these. I may have one or I may skip it.***
- 2 x Arduino Nano, **5V**, 16 mHz, ATMEGA328 or similar
    - One for the bot and one for the controller
    - **The instructions repeatedly refer to the Nano, but the Pro Mini also works!**
        - **If you use  Pro Mini you must have an FTDI cable of some sort!**
    - This comes in both 5V and 3.3V variants. **Be sure to get the 5V variant.**
    - DC input 3.3V up to 12V, so the controller can run directly from a 9V battery.
    - I went with the Pro Mini.
    - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/collections/arduino-and-shields/products/arduino-pro-mini-atmega328-5v-16mhz-unsoldered)
    - [Adafruit](https://www.adafruit.com/product/2378) - $14
    - [Amazon Search](https://www.amazon.com/s?k=arduino+pro+mini+328)
    - **[Amazon Item](https://www.amazon.com/HiLetgo-Atmega328P-Replace-ATmega128-Atmega328/dp/B07X2JGS69/)**
        - 3 for $14
        - [[attachments/b19d564c1d25c300c361d79043049801_MD5.jpg|HiLetgo Pro Mini Atmega328P]]
![attachments/b19d564c1d25c300c361d79043049801_MD5.jpg](/img/user/attachments/b19d564c1d25c300c361d79043049801_MD5.jpg)
 
- "FTDI" USB to Serial Cable/Board
    - If you use an Arduino Nano, it has USB but in, but if you get the Pro Mini you need your own "FTDI" USB to Serial adapter.
    - These can come as a board with a USB plug and pins on it or as a USB cable with separate or connected pins on the other.
    - "FTDI" is a brand name, but it is the most common type or cloned type, so it shows up a lot.
    - [Amazon Search](https://www.amazon.com/s?k=ftdi+usb+to+serial)
            - I would **probably** get one of these now as it is easy to adapt it with your own USB cable and the jumper wires you are already buying and it had good reviews.
        - **[Amazon Item](https://www.amazon.com/gp/product/B07BBPX8B8/)**
    - Because I already have a few of these, I didn't have to buy one, so read reviews and pick one and then read up on it. 
- Rotary potentiometer, 10K Ohms, 6mm shaft diameter, with 3 wires pre-soldered. Also, matching dial cap and nut.
    - These are very generic and can be found all over the place.
    - Note the little metal bit that sticks out on one side and fits into the hole in the 3D printed hexabot body to hold it in the right place while you twist the knob.
    - **[Amazon Item](https://www.amazon.com/dp/B07B64MWRF?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_1)** that I have used for years for many projects, including this one.
        - *Note: Unlike the rest of the parts listed, I already owned this set of potentiometers, so it was not picked specifically for this project, but it works.*
        - I didn't fret about the knob "matching", although I also already have a collection of knobs from various places to I just picked one that I liked.
- 2 x HC05 Bluetooth Module with 4 x F-F jumper wires for making connections (Note: the HC05 has six pins but only four are used in this project.)
    - One for the bot and one for the controller
    - There is a note [here](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Battery/Switch_Construction) about this needing to operate on 5 volts, which maybe not all of them do?
    - [Guide](https://en.hwlibre.com/Complete-guide-to-the-HC-05-and-HC-06-Bluetooth-modules-for-Arduino./)
    - [Amazon Search](https://www.amazon.com/bluetooth-module-hc05/s?k=bluetooth+module+hc05)
    - **[Amazon Item](https://www.amazon.com/dp/B07VL725T8)**
        - "*Input voltage: 3.6V--6V, prohibit exceeding 7V*"
        - So it should work be fine with 5 volts.
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
            - Note that the Vorpal information doesn't measure them quite the same way as everyone else, who generally call these "10x15mm" switches.
        - [Vorpal Store](https://vorpal-robotics-store.myshopify.com/products/on-off-rocker-switch-pack-of-2)
        - **[Amazon Item](https://www.amazon.com/10pcs-10x15mm-Rocker-Switch-Black/dp/B079JC8HKH/)** - It is called "10x15mm", but seems to work. Here are the measurements from the Amazon site in case it helps in the future:
            - [[attachments/799a1314ced07b1745361ac5cbe957f2_MD5.jpg|Open: Pasted image 20260116215138.png]]
![attachments/799a1314ced07b1745361ac5cbe957f2_MD5.jpg](/img/user/attachments/799a1314ced07b1745361ac5cbe957f2_MD5.jpg)
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
   - Jumper or "Shunt"
       - [Amazon Search](https://www.amazon.com/s?k=computer+jumper&crid=17TZ0J8UHSMS8&sprefix=computer+jumper)
       - [Amazon Item](https://www.amazon.com/California-JOS-Standard-Circuit-Connection/dp/B0BRK36G33)
       - You are going to need one small jumper for the servo controller board. You could also just wrap some wire around the pins indicated in the instructions and solder it.
       - I already have a ton of jumpers going back to the 1980's, but if you don't have any and don't know what they are, they look like this:
       - [[attachments/40fd2d0d3ed89e4198550b97ab3a31cb_MD5.jpg|Open: Pasted image 20260117175130.png]]
![attachments/40fd2d0d3ed89e4198550b97ab3a31cb_MD5.jpg](/img/user/attachments/40fd2d0d3ed89e4198550b97ab3a31cb_MD5.jpg)
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
### Fasteners
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
#### Electronics
  - 9v Battery Clip
       - **[Amazon Item](https://www.amazon.com/dp/B08SL9X2YC/)**
   - 1 x 4x4 button matrix with associated connecting wires. The matrix we use is marked YL-102 in the corner. See the picture. It's blue and has the keys number K1 through K16. You may be able to use others but the pin numbers may differ.
       - ![attachments/6ae0e68361352a67b9c479e137d94cf3_MD5.png](/img/user/attachments/6ae0e68361352a67b9c479e137d94cf3_MD5.png)
       - I was not able to find this exact item anywhere at all, so I purchased this similar item from Amazon:
           - **[Amazon Item](https://www.amazon.com/dp/B07QKCQGXS/)**
                - The Gamepad Button Carrier and Cover must be modified to fit this.
                - [[attachments/c03f349f1993f4b911d7df76a3b20e1a_MD5.jpg|Open: Pasted image 20260121170508.png]]
![attachments/c03f349f1993f4b911d7df76a3b20e1a_MD5.jpg](/img/user/attachments/c03f349f1993f4b911d7df76a3b20e1a_MD5.jpg)
- 1 x Dpad Button module with associated connecting wires. The one we use is marked Keyes_AD_Key and has yellow buttons and a red circuit board. See picture.
    - ![attachments/335247a1239aee2026229ad40eb0f72c_MD5.png](/img/user/attachments/335247a1239aee2026229ad40eb0f72c_MD5.png)
    - I could not find these on Amazon, but I found them on eBay, so I purchased this one item via Ebay:
        - **[eBay Item](https://www.ebay.com/itm/383572603225)**
    - Based on my testing this Dpad aligns with the "STDDPADSTYLE" in the Vorpal code, so it should work fine.
- 1 x microSD Card Reader module and six wires to connect it, and a microSD card that is compatible with the Arduino SD library. A microSD card is required for record/play features to work. The capacity should be 2 gb or less, either SD or SDHC format. The gamepad can be used to format the card for use by Arduino (hold down W4 while booting the gamepad, count to 10 slowly, release W4).
    - **[Amazon Item](https://www.amazon.com/HiLetgo-Adater-Interface-Conversion-Arduino/dp/B07BJ2P6X6/)**
        - Note: These come in packs of five, and you only need one! Don't over-order like I did.
#### Fasteners
- 4 x #6-32 x 1/2" screw to hold cover on gamepad
    - Note that you will see references to screws to hold the switch in, but the current model does not use them.
    - **[Amazon Item](https://www.amazon.com/dp/B0D2ZZVLRL)**
## 3D Printed Parts
Again, the link to Vorpal's Dropbox folder which contains their STL files is on their Wiki [Vorpal Hexapod Source Files](https://vorpalrobotics.com/wiki/index.php?title=Vorpal_Hexapod_Source_Files)

The Controller ("Gamepad") Button Carrier and Cover would not fit the button matrix that I purchased from Amazon, so I modified them to fit.
 - [Expanded Gamepad Button Carrier](https://ekpyroticfrood.net/public-files/vorpal-hexabot/Gamepad_V1r9a_Button_Carrier_Expanded_for_Tegg_Matrix.stl)
 - [Expanded Gamepad Cover](https://ekpyroticfrood.net/public-files/vorpal-hexabot/Gamepad_V1r9a_Cover_Expanded_for_Tegg_Matrix.stl)
# HC-05 Preparation
Since we didn't buy the bits from Vorpal, we need to configure the HC-05 modules in the way that is expected by the software.
It is best to get this done before putting things together, as you will need to have full access to them.

**Note: According to the video and instructions, the *Master* goes in the remote control.**

You can use the FTDI adapter to connect your computer to the HC-05 and change its settings.
Connect like this:
[[attachments/cf0c76d7a362048878c2f48634ca0b03_MD5.jpg|Open: Pasted image 20260117225653.png]]
![attachments/cf0c76d7a362048878c2f48634ca0b03_MD5.jpg](/img/user/attachments/cf0c76d7a362048878c2f48634ca0b03_MD5.jpg)
The image shows a breakout board style FTDI connector, but you can do it with other types. I used a breadboard to jumper the correct pins like this:
[[attachments/610a0dd09a1f9a68dc8bc863466fae07_MD5.jpg|Open: Pasted image 20260118121152.png]]
![attachments/610a0dd09a1f9a68dc8bc863466fae07_MD5.jpg](/img/user/attachments/610a0dd09a1f9a68dc8bc863466fae07_MD5.jpg)

We will put the board into "AT" mode and set one to "Slave" (0) and get its address. Then we will set the other one to "Master" (1) and provide it with the "Slave's" (0) address to connect to.

Note that there are many online resources about these boards, and you will find that not all commands work with all boards. Hopefully this process will work with your board.

You may also see mention of hooking up another pin to 3.3v, but you **do not need to do that.** Just the 5V, Ground, TX and RX are all that you need.

This video covers the procedure very well, except that they use another Arduino instead of the FTDI cable to connect the computer to the HC-05 for programming. You can certainly do that, but I just used the FTDI cable as diagrammed above and instructed below.

Perform this on the "Slave" (0) first, as you need to get it's address for entry into the "Master" (1) later:

- Open the Arduino IDE
- Connect Bluetooth to PC using FTDI led will flash fast
- Set the Board to "Arduino BT"
- Choose your COM port
- Set the baud to 38400
- Disconnect only VCC wire from the Bluetooth
- Push and hold the button on Bluetooth while connecting the VCC wire to get into AT-mode
- Once you get into AT-mode, led will flash slower
- Open Serial Monitor (Tools-Serial Monitor)
- On the bottom select "Both NL & CR" and "38400 baud"
- In the TextBox type AT and hit Enter or click Send you should get OK
- AT+UART?
    - Both devices should say +UART:38400,0,0 as that is the default and that is correct for our use.
- Slave (hexapod)
    - AT+ROLE?
        - Should respond with +ROLE:0 indicating that it is the slave.
    - AT+ADDR?
        - Write down the address it returns, which will be like this:
        - +ADDR:98D3:02:969A17
    - That is all for the Slave, you can disconnect it and set it aside for use in the hexapod
- Master
    - AT+ROLE?
        - Presumably it will also respond with +ROLE:0, but we want to change this one.
    - AT+ROLE=1
        - It should respond "OK"
    - AT+ROLE?
        - Now it should respond with +ROLE:1
    - AT+CMODE?
        - Presumably it will respond with +CMODE:1
            - 1 = Connect to ANY partner
            - 0 = Connect to ONE partner
            - So we want to change it.
    - AT+CMODE=0
        - It should respond "OK"
    - AT+CMODE?
        - Now it should respond with +CMODE:0
    - AT+BIND=98D3,02,969A17
        - Replace the part after the equal sign with the address we obtained from the "Slave"
        - Be sure to replace the :'s with commas
    - AT+BIND?
        - This should return the address that you entered

*Note that if you leave the device alone for too long without sending any commands it will reset to "normal" non-AT mode and you will have to unplug it, hold the button, and plug it in again to get back to AT mode.*

Later when things are built, I suggest testing the bluetoot modules before buttoning things up. With only power to them, they should connect to each other, even if they are not connected to their devices.
Their lights will indicate how they are doing:
- NOT CONNECTED: When the Bluetooth modules are not connected, there will be a fast, steady blink.
- IN THE PROCESS OF CONNECTING: When they first start to connect, they will blink slowly at first, then will go dark for a couple of seconds. This process will only take about 5 seconds.
- CONNECTED: When they are properly connected, then there will be a 2 second pause followed by two quick blinks, and this will repeat over and over as long as there is a connection. **This is the one you want to see.** If you don't, try the procedure above again.
You can double check by disconnecting and reconnecting the power to one module. The other one should quickly go to fast blinking, and when you power the one back on they will both fast blink for a bit until both start blinking the slower "connected" indication.
# Arduino Software
The Arduino code, along with other files needed for the project are linked from the Vorpal Wiki under [Vorpal Hexapod Source Files](https://vorpalrobotics.com/wiki/index.php?title=Vorpal_Hexapod_Source_Files).

The software is contained in both their Dropbox Folder and their Github repository, both linked above. I used the files from the Dropbox folder myself.

The Arduino .ino files to use are in:
`SOFTWARE_HEXAPOD/SOFTWARE_HEXAPOD_CURRENT_RELEASE_V3r1c/Vorpal-Hexapod-Gamepad/Vorpal-Hexapod-Gamepad.ino`
and
`SOFTWARE_HEXAPOD/SOFTWARE_HEXAPOD_CURRENT_RELEASE_V3r1c/Vorpal-Hexapod-Robot/Vorpal-Hexapod-Robot.ino`
## Changes
I had to make these changes to the code for it to work with my hardware. Obviously test and experiment first, but I include these here to hopefully save you time in case you run into the same issues.
### Bluetooth Baud Rate on BOTH
On both sets of code (Controller and Hexapod) I had to change the line that reads:
`BlueTooth.begin(38400);`
to
`BlueTooth.begin(9600);`

Without this change the controller was not able to communicate with the hexapod.

I haven't figured out why yet, just that this works.
### Dpad Settings on Controller Code
Despite my controller appearing to conform to the "STDDPADSTYLE" in every way, including the output, I found that the code kept switching to "ALTDPADSTYLE" causing my controller to incorrectly identify inputs.

To solve this, on the controller code I had to delete or comment out lines 1176-1209:
```
  int dp = analogRead(DpadPin);
  Serial.println(dp); // uncomment this if you're having trouble with DPAD autodetect
  if (dp < 850) { // some dpad button is being held
    Serial.print("#DPA"); // DPAD AutoDetect
    if (dp > 250 && dp < 500) { // Alternative dpad detected
      DpadStyle = ALTDPADSTYLE;
    } else if (dp > 600 && dp < 850) { // standard dpad
      DpadStyle = STDDPADSTYLE;
    } else {
      Serial.println(dp); // not detected, something's wrong, just leave it at the default
    }
    EEPROM.update(0, DpadStyle); // save for future boots
    //Serial.println("EEUPDATED");
  } else {
    // check to see if a prior dpad style has been selected and stored in the
    // EEPROM at position 0
    byte dp = EEPROM.read(0);
    Serial.print("EE0="); Serial.println(dp);
    if (dp < NUMDPADSTYLES) { // any value greater or equal to NUMDPADSTYLES is invalid
      DpadStyle = dp;
      Serial.print("#DPE"); // DPAD EEPROM detect
    } else {
      Serial.print("#DPI"); // DPAD internal default
    }
  }
  if (DpadStyle == STDDPADSTYLE) {
      Serial.println("ST"); // standard dpad
  } else {
      Serial.println("AL"); // alternative dpad
  }
```
Essentially forcing the use of the default "STDDPADSTYLE" under all circumstances.

## Upload

You will want to upload the code to both devices before building as they can be fiddly to access after building and you will need the software on the hexapod for part of the build process.

The install is a pretty typical Arduino install.

**The one gotcha I ran into** is that it will complain that it is missing the SDFat library.
[[attachments/561d80f787cde5df586722313d83bd37_MD5.jpg|Open: Pasted image 20260118121851.png]]
![attachments/561d80f787cde5df586722313d83bd37_MD5.jpg](/img/user/attachments/561d80f787cde5df586722313d83bd37_MD5.jpg)
**Install this from the downloaded ZIP file** using the menu: 
Sketch->Include Library -> Add .ZIP library
[[attachments/5f986f6cec5304d6bf177afc6c91de88_MD5.jpg|Open: Pasted image 20260115155840.png]]
![attachments/5f986f6cec5304d6bf177afc6c91de88_MD5.jpg](/img/user/attachments/5f986f6cec5304d6bf177afc6c91de88_MD5.jpg)
If you try to use any other SdFat library, for instance one that you can get via the Arduino Library Manager:
1. It probably still won't build.
2. If you do manage to get it to build, the result may be too large for your Arduino Mini board's memory.

It may ask for other libraries, and again, I installed everything from the included ZIP files, which is a better guarantee of things working than if you pull down newer version automatically.

I did not have to modify the code in any way to get it to upload to my boards.
# Debugging and Troubleshooting Code
There are a several debug variables in the code at the top.
I set and watched these to sort out issues with my controller.

Remember when using the Serial Monitor in the Arduino IDE to set the terminal to *9600 baud*.

When I was trying to sort out the HC-05 issues I used this code:
 - Controller:
```
#include <SoftwareSerial.h>
SoftwareSerial BlueTooth(A5,A4);

void setup() {
  Serial.begin(9600);
  BlueTooth.begin(9600);
}

int number = 0;
void loop() {
  Serial.print(number);
  BlueTooth.print(number);
  number++;
  if (number > 9) {
    number = 0;
  }
  while (BlueTooth.available()) {
    Serial.write(BlueTooth.read());
  }
  Serial.println("");
  delay(500);
}
```
 - Robot
Use the exact same code, but change the second line to:
`SoftwareSerial BlueTooth(A5,A4);`
to account for the differing pin location of the HC-05

When run this will simply print 0 to 9 continuously in the first "column" and then print 0 to 9 next to it **if** it is receiving from the other side.
If it is not receiving, you will just see one digit. If it is receiving you will see two digits.
They don't need to match, as there is no timing code here.

In my case what I got was garbage instead of the second character until I changed both `BlueTooth.begin` lines to `9600`.
# Build
I followed the YouTube videos provided on the [Vorpal The Hexapod Assembly Instructions](https://www.vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Assembly_Instructions#VIDEO_BUILD_INSTRUCTIONS) page along with reading over the page for understanding and to clarify details that I didn't get from the videos.

 - Note that the video includes the old style power switch that had its own extra 3D printed part. The current design does away with that and the switch just pops in. This is covered in the Assembly Instructions page.
## Wiring
You will need to solder up the various bits yourself.
I've made some notes below, but read the linked instructions before proceeding.
### Switches
The battery and switch instructions are [here](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Battery/Switch_Construction) which is a little confusing as most of the rest of the instructions are elsewhere.

I've copied the schematics for my own benefit, but be sure to read the instructions before assembly!
#### Gamepad Switch
[[attachments/76717b160119fb1c14276a836fbb5296_MD5.jpg|Open: Pasted image 20260116175401.png]]
![attachments/76717b160119fb1c14276a836fbb5296_MD5.jpg](/img/user/attachments/76717b160119fb1c14276a836fbb5296_MD5.jpg)
#### Hexapod Switch
[[attachments/de64ff234d0cd9c294e603c6c95bc70c_MD5.jpg|Open: Pasted image 20260116175444.png]]
![attachments/de64ff234d0cd9c294e603c6c95bc70c_MD5.jpg](/img/user/attachments/de64ff234d0cd9c294e603c6c95bc70c_MD5.jpg)
 - Switch -> UBEC 3pin: 5 inches - "*You need at least 5 inches (125mm) of wire from the switch to the end of the three pin Dupont Connector coming off the UBEC.*"
 - Battery Holder -> Switch: 5 inches - "*The battery holder needs to also have roughly 5 inches (125mm) of wire between it and the switch so you have enough room to bring the cable up and connect to the battery.*"
### UBEC
Note that the bare wires are typically the unregulated voltage input and the 3-pin connector is the regulated voltage output.
### Potentiometer
The potentiometer is also covered on the battery and switch instructions page [here](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Battery/Switch_Construction).

[[attachments/9a185c1592a90cc94356bff5e46a41ea_MD5.jpg|Open: Pasted image 20260116175548.png]]
![attachments/9a185c1592a90cc94356bff5e46a41ea_MD5.jpg](/img/user/attachments/9a185c1592a90cc94356bff5e46a41ea_MD5.jpg)
_Analog Pins:_
- A0 Potentiometer signal (white wire)
- A1 Potentiometer Power (red wire)
- A2 Potentiometer Ground (black wire)
The "signal" wire is the **middle** connector on the potentiometer.
The ground and power are the outer two pins, and it **does not matter** which you wire up to which.
### Arduinos
The wiring diagrams are also on the same page, but here they are again for my own reference. I had to reference the image of my board and these a lot as the pins are not in the same location on the Pro Mini that I used.
[Arduino Pro Mini Information](https://docs.arduino.cc/retired/boards/arduino-pro-mini/)
- [[attachments/b19d564c1d25c300c361d79043049801_MD5.jpg|HiLetgo Pro Mini Atmega328P]]
![attachments/b19d564c1d25c300c361d79043049801_MD5.jpg](/img/user/attachments/b19d564c1d25c300c361d79043049801_MD5.jpg)
 
 [[attachments/4c37333aff4540361ddce4bcc0dbd4fa_MD5.jpg|Vorpal Hexapod Arduino Wiring Diagram Image]]
![attachments/4c37333aff4540361ddce4bcc0dbd4fa_MD5.jpg](/img/user/attachments/4c37333aff4540361ddce4bcc0dbd4fa_MD5.jpg)
[Vorpal Hexapod Arduino Wiring Diagram Link](https://www.vorpalrobotics.com/wiki/images/5/51/Hexapod-Nano-Diagram.JPG)
 - The "(AP)" connections are for the "Accessory Port". I personally skipped these on my first build.
 - I also skipped the "Buzzer Signal" on my first build.

[[attachments/bcb482f130a55499e3dc593f383a3556_MD5.jpg|Vorpal Controller Arduino Wiring Diagram Image]]
![attachments/bcb482f130a55499e3dc593f383a3556_MD5.jpg](/img/user/attachments/bcb482f130a55499e3dc593f383a3556_MD5.jpg)
[Vorpal Controller Arduino Wiring Diagram Link](https://www.vorpalrobotics.com/wiki/images/8/86/Gamepad-Nano-Diagram-v3.JPG)

**Note some pin translations from Nano (documents) to Pro Mini (what I got):**
 - VIN = RAW
 - VCC = +5V
### Button Matrix (On Controller)
If you are using this common Button Matrix:
[[attachments/c03f349f1993f4b911d7df76a3b20e1a_MD5.jpg|Open: Pasted image 20260121170523.png]]
![attachments/c03f349f1993f4b911d7df76a3b20e1a_MD5.jpg](/img/user/attachments/c03f349f1993f4b911d7df76a3b20e1a_MD5.jpg)
Wiring is pretty simple, as follows:
 - R4 <-> Arduino D2
 - R3 <-> Arduino D3
 - R2 <-> Arduino D4
 - R1 <-> Arduino D5
 - C1 <-> Arduino D6
 - C2 <-> Arduino D7
 - C3 <-> Arduino D8
 - C4 <-> Arduino D9
This will result in a straight row of wires, pin to pin, from the controller to the one side of the Arduino.
This places the buttons in the output expected by the code.

Ignore the "S1" to "S16" labels on the board as the Vorpal software views them differently, and that is what matters.
### Servo Controller
The servo controller wiring is documented very well on the main [hexapod assembly instruction page](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Assembly_Instructions).

Something "odd" to note is that power is supplied **IN** via servo port 12. That power is then guided to the controller logic boards via a "shunt" or jumper across the V+ and VCC pins.
This might look very strange, but it is pretty standard for servo controllres.

My servo controller did not have the servo port numbers printed on the board, so the diagram on the site is quite helpful, and is copied here.
[[attachments/bc5febb27fafb82cc97d9cc18ec23f0f_MD5.jpg|Open: Pasted image 20260117174747.png]]
![attachments/bc5febb27fafb82cc97d9cc18ec23f0f_MD5.jpg](/img/user/attachments/bc5febb27fafb82cc97d9cc18ec23f0f_MD5.jpg)
On the servos, yellow is the signal wire, which may look orange.
Brown also stands in for black as the ground wire.
# SD Card Reader
I have not installed or tested the SD Card reader yet!
# Trim
Don't forget to [trim your hexapod settings](https://vorpalrobotics.com/wiki/index.php/Vorpal_The_Hexapod_Trim_Mode_Guide) when you are done building it.
