---
{"title":"Propeller Code for Arlobot (PropWare Version)","created":"2020-08-27","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/arlobot/propeller-code-for-arlobot-prop-ware-version/","dgPassFrontmatter":true}
---

*Posted: August 27, 2020*

While a lot of the fun stuff with the robot happens on the Ubuntu laptop with ROS, the motor control and sensor polling is all done on a Parallax Propeller microcontroller.

I like to think of the laptop as the cerebral cortex of the robot's brain and the Propeller board as the Cerebellum.

The code for the Propeller is all written in C. I have set it up so that it will refuse to run into things even if ROS tells it to, and if it gets much too close to an object it will actually back away. This way it is safe to experiment with ROS without worrying too much about crashing into walls. You can also gently "push" the robot out of your way by just getting close to it and it will move away if it can. (Yes, you can "herd" your robot!) Obviously you still need to be careful, especially if you tell it to drive around extremely fast, because you can drive into a wall faster than the sensors are able to register it.

Here are the steps to get the C code that I use with my [Arlobot ROS package](https://github.com/chrisl8/ArloBot) onto your robot's Propeller board using the Ubuntu laptop you should have connected to it.

Follow all of these steps from your Ubuntu laptop. Because the laptop must be connected to the Propeller board via USB at all times for ROS to operate, it is natural to update the code on the Propeller board from the laptop when needed.

**Update:**  
The **only** thing you need to do now is run the script `install_Propeller_code.sh` to automatically install the required code to your Propeller Activity Board.

_Everything below is useful information, but if the script above worked, you can stop reading this page now and move on to testing your robot with `PropellerSerialTest.sh`_ and then use the Web Interface to run the robot_._

* * *

**0\. PropWare Background Information**

_You can skip step 0 if you like, and come back if you need more information. Everything here is background information, not things you need to do._

  
Parallax used to support Linux, but they have not maintained their Linux support for some years now. If you follow any Linux links on their site you will find a dead end of old broken code.

If you want to use Windows and SimpleIDE, you can follow the old [[SimpleIDE Version)](Propeller Code for Arlobot (SimpleIDE Version\|Propeller Code for Arlobot (SimpleIDE Version)]].md) instructions. Otherwise we will use a third party system called "PropWare" to install the code to our Propeller Board from Linux.

**Please note that this is all background information. The installation of PropWare was done via the noetic-setup script already.**

- The latest version of Propware should be available here under the Download link for Ubuntu: [[https://david.zemon.name/PropWare/#/download](https://david.zemon.name/PropWare/\|https://david.zemon.name/PropWare/#/download](https://david.zemon.name/PropWare/#/download]]
    - However, the Propware site and download link are usually broken, so you may have to contact [https://forums.parallax.com/profile/DavidZemon](https://forums.parallax.com/profile/DavidZemon) and ask for a working link.
    - At this time it is: [https://ci.zemon.name/repository/download/PropWare\_Develop/3817:id/propware\_3.0.0.224-1\_all.deb?guest=1](https://ci.zemon.name/repository/download/PropWare_Develop/3817:id/propware_3.0.0.224-1_all.deb?guest=1)
    - There is also a backup copy here: [https://www.dropbox.com/s/12l51adhwge1y43/propware\_3.0.0.224-1\_all.deb?dl=1](https://www.dropbox.com/s/12l51adhwge1y43/propware_3.0.0.224-1_all.deb?dl=1)
    - _Remember, you do not need to do this, it was already done by the noetic-setup script._
- To install PropWare:
    - `sudo dpkg -i sudo dpkg -i propware_3.0.0.224-1_all.deb`
    - _Remember, you do not need to do this, it was already done by the noetic-setup script._
- You **also** need PropGCC which you can download from:
    - [https://ci.zemon.name/repository/download/PropGCC5\_Gcc4linuxX64/3620:id/propellergcc-alpha\_v1\_9\_0-gcc4-linux-x64.tar.gz?guest=1](https://ci.zemon.name/repository/download/PropGCC5_Gcc4linuxX64/3620:id/propellergcc-alpha_v1_9_0-gcc4-linux-x64.tar.gz?guest=1)
    - Thre is also a backup copy here: [https://www.dropbox.com/s/sccr5cs46hgrlwd/propellergcc-alpha\_v1\_9\_0-gcc4-linux-x64.tar.gz?dl=1](https://www.dropbox.com/s/sccr5cs46hgrlwd/propellergcc-alpha_v1_9_0-gcc4-linux-x64.tar.gz?dl=1)
    - The easiest thing is for it to be in /opt/parallax. The other option is for it to be in your path.
        - (NOTE: SimpleIDE used to put these same files in /opt/parallax when it was installed, so that will replicate the same behavior.)
    - To install PropGCC:
        - `sudo cp ~/Downloads/propellergcc-alpha_v1_9_0-gcc4-linux-x64.tar.gz /optcd /optsudo tar xvf propellergcc-alpha_v1_9_0-gcc4-linux-x64.tar.gzsudo rm /opt/propellergcc-alpha_v1_9_0-gcc4-linux-x64.tar.gz`
        - _Remember, you do not need to do this, it was already done by the noetic-setup script._

**Now you can work through the steps here to prove that it works and learn how to make new projects:**

[[https://david.zemon.name/PropWare/#/getting-started](https://david.zemon.name/PropWare/\|https://david.zemon.name/PropWare/#/getting-started](https://david.zemon.name/PropWare/#/getting-started]]  
They really do work. ;)  
The TL;DR: is:

1. cd to the folder with your code.
2. Make a CMakeList.txt file
3. `mkdir bin; cd bin`
4. and then every time you want to test your build:  
    `rm -rf *;cmake -G "Unix Makefiles" ..;make debug`

This site will give some clues about translating settings from .side files to CMakeList.txt, such as memory model and board type: [[https://david.zemon.name/PropWare/#/reference/cmake-by-example](https://david.zemon.name/PropWare/\|https://david.zemon.name/PropWare/#/reference/cmake-by-example](https://david.zemon.name/PropWare/#/reference/cmake-by-example]]

The various make directives decide where to send the code (RAM or EEPROM) and what to do after sending it:

- run: Load the executable to EEPROM and execute the code.
- run-ram: Load the executable to HUB RAM and execute the code.
- run-sd-loader: Load the executable to SD card, and execute the code.
- run-sd-cache: Load the executable to SD card, use it as a cache, and execute the code
- debug: Load the executable to HUB RAM, execute the code, and open an interactive serial terminal
- debug-eeprom: Load the executable to EEPROM, execute the code, and open an interactive serial terminal
- debug-sd-loader: Load the executable to SD card, execute the code, and open an interactive serial terminal
- debug-sd-cache: Load the executable to SD card, use it as a cache, execute the code, and open an interactive serial terminal
- gdb: Load the executable to HUB RAM and start GDB

TL;DR:  
**`make` - build without attempting to load it anywhere (No Propeller board)  
`make debug` - load to Propeller board, but do NOT overwrite EEPROM (for testing)  
`make run` - load it to EEPROM for permanent use**

**1\. Add your user to the "dialout" group**  
Otherwise you will not have access to /dev/ttyUSB0

`sudo adduser [your_user_name] dialout  `
i.e.  
`sudo adduser chrisl8 dialout` 
﻿

And then you will have to reboot to make this work.  
_NOTE: The setup-noetic script probably did this for you._

**2\. Edit the Propeller C Code for Arlobot to fit your setup.**  
In whatever editor open up `~/.arlobot/per_robot_settings_for_propeller_c_code.h`  
Now at the top there is an entire section of "#define" statements.  
You need to comment out some for items you don't have, and you need to adjust the numbers after others to indicate things like how many PING sensors you have and where they are located.  
By doing this, the code will be compiled to only include the parts you need and with setting specific to your robot.

**3\. Load Propeller C Code for Arlobot on to Propeller board.**  
The way the Propeller controller works is that if you load a program into "EEPROM" it will stay there and start any time the board is reset or power cycled. This means once the code is there you don't have to mess with it again unless you want to change something.

Plug the USB cable into the Activity Board and Ubuntu Laptop.

```
cd ~/catkin\_ws/src/ArloBot/PropellerCodeForArloBot/ROSInterfaceForArloBot/
mkdir bin
cd bin
rm -rf \*
cmake -G "Unix Makefiles" ..
make run # Remember, make run installs it to EEPROM
```
  
The board should load the code and reset.

If you get any of the "#define" settings wrong the first time, this could be one reason to reload it.

**9\. Testing.**  
A good way to test your Propeller code is to run:

```
cd ~/catkin\_ws/src/ArloBot/scripts/  
./PropellerSerialTest.sh
```

It will start a test engine for testing everything about your robot before trying to run ROS.

Test all output, and attempt sending twist commands directly.  
Until this works, do not expect ROS to work.

**All done!**

Remember, this is open source, so feel free to fix mistakes and make changes to the code and tell me about them! Better yet, fork the code and send me pull requests!  
Next read over README.md, or try scripts from ~/catkin\_ws/src/ArloBot/scripts/ and anything else from ROS that you want to try!

Finally don't forget the web interface to your robot!  

**P.S. [[Ancient History/2015/Prevent Propeller Activity Board from running on USB Power\|Prevent Propeller Activity Board from running on USB Power.md]]**   
You may want to do this if you ONLY want the the Propeller Board to run from DC power and not the USB device.
