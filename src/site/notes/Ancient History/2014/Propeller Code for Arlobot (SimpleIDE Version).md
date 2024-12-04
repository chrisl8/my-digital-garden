---
{"title":"Propeller Code for Arlobot (SimpleIDE Version)","created":"2014-12-29","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2014/propeller-code-for-arlobot-simple-ide-version/","dgPassFrontmatter":true}
---

*Posted: December 29, 2014*

**WARNING: OLD VERSION!  
You should use the [Propeller Code for Arlobot (PropWare Version)](Propeller%20Code%20for%20Arlobot%20(PropWare%20Version).md) now.**

While a lot of the fun stuff with the robot happens on the Ubuntu laptop with ROS, the motor control and sensor polling is all done on a Parallax Propeller microcontroller.

I like to think of the laptop as the cerebral cortex of the robot's brain and the Propeller board as the Cerebellum.

The code for the Propeller is all written in C. I have set it up so that it will refuse to run into things even if ROS tells it to, and if it gets much too close to an object it will actually back away. This way it is safe to experiment with ROS without worrying too much about crashing into walls. You can also gently "push" the robot out of your way by just getting close to it and it will move away if it can. (Yes, you can "herd" your robot!) Obviously you still need to be careful, especially if you tell it to drive around extremely fast, because you can drive into a wall faster than the sensors are able to register it.

Here are the steps to get the C code that I use with my [Arlobot ROS package](https://github.com/chrisl8/ArloBot "Arlobot Github Repository") onto your robot using the Ubuntu laptop you should have connected to it.

Follow all of these steps from your Ubuntu laptop. Because the laptop must be connected to the Propeller board via USB at all times for ROS to operate, it is natural to install SimpleIDE on the laptop and use it to update the code on the Propeller board when needed.

**0\. Learn first!**  
This isn't a store bought toy, this is a learning project, so if you have never done anything at all with a Propeller board, I highly recommend **insist** that you go to [http://learn.parallax.com/propellerc](http://learn.parallax.com/propellerc "Learn Parallax Propeller C") and follow some of the turtorials to get to know the Propeller chip, the Activity Board, SimpleIDE and Propeller C.  
This will give you a good background to understand what is going on.  
You can do this with just the Activity Board and your Windows computer, and then come back here later to make it all work with your Ubuntu laptop.  
Without doing at least a few of the tutorials you will be following my instructions in the dark. They may get you to your destination, but it will be frustrating.

**1\. Add your user to the "dialout" group**  
Otherwise SimpleIDE tells you that you have no access to /dev/ttyUSB0

sudo adduser \[your\_user\_name\] dialout
i.e.
sudo adduser chrisl8 dialout

And then you will have to reboot to make this work.

**2\. Set up Parallax SimpleIDE for Linux**

_**FYI: Parallax has abandoned support for Linux, as can be seen from this thread:**_  
[http://forums.parallax.com/discussion/166656/simpleide-on-linux](http://forums.parallax.com/discussion/166656/simpleide-on-linux)

I am very sad about this, but it seems we can limp along by using [copies of old code releases](https://web.archive.org/web/20161005174013/http://learn.parallax.com/tutorials/language/propeller-c/propeller-c-set-simpleide/linux).

In the example below I show using 'wget' to pull the latest version of SimpleIDE from a web archive service (since Parallax has abandoned it) and installing the package on Ubuntu.

```
sudo apt install libftdi1
wget https://web.archive.org/web/20161005174013/http://downloads.parallax.com/plx/software/side/101rc1/simple-ide\_1-0-1-rc1\_amd64.deb
sudo dpkg -i simple-ide\_1-0-1-rc1\_amd64.deb
```

**3\. Test SimpleIDE**  
If it is not already done, plug your Propeller board into your Ubuntu laptop with the USB cable.

Open a terminal window in the Ubuntu desktop and run:

simpleide

**IF** you get errors about missing dependencies, you may need to run:

sudo apt --fix-broken install

The first time SimpleIDE runs it will create a folder with required libraries in it.  
Please let it use the default location.

![SimpleIDE-Welcome](/img/user/attachments/SimpleIDE-Welcome.png)

SimpleIDE should open with a "Hello World" program called Welcome:  
  
Notice that I am using VNC to do this from the comfort of my desktop machine.

Make sure you see "/dev/ttyUSB" at the top right. It will probably be USB0, but if you have more than one board it could be another one.

![SimpleIDE-TerminalRun](/img/user/attachments/SimpleIDE-TerminalRun.png)

Just run it with the terminal by pressing the blue terminal with the "play" arrow in it:

You should get a blue terminal window with the text "Hello!" in it, or whatever the simple test program was set up to send.  
This proves that your SimpleIDE is installed and that your Propeller board is properly connected.  
You can press "OK" on the Terminal window to close it and close SimpleIDE.

**4\. Add Arlo Code to SimpleIDE**  
For HB-25: The extra code from Parallax to work with the Arlo platform is already in my arlobot repository, you just need to copy it into your SimpleIDE folder structure.  
If you already ran SimpleIDE once, and if you let SimpleIDE use default locations, this should work for you:

\# Do NOT run these lines unless you have the OLD HB-25 motor controllers!
# cd ~/catkin\_ws/src/ArloBot/ArloBotParallaxLibraries/
# or if that does not exist
# cd ~/catkin\_ws/src/ArloBot/OldArloBotParallaxLibrariesForHB25/
# ./PutFilesInPlace.sh

The library from Parallax to work with the Arlo platform is in a separate download on the Parallax site. Run these commands to download and "install" the library:  
_(NOTE: This copies files to the default folder created when you ran SimpleIDE for the first time.)_

```
cd
wget http://learn.parallax.com/sites/default/files/download/1350/28966-Arlo-with-Activity-Board-2016-05-02a.zip
unzip 28966-Arlo-with-Activity-Board-2016-05-02a.zip
mv 28966-Arlo-with-Activity-Board-2016-05-02a/Arlo-with-Activity-Board-200502a/libarlodrive/ ~/Documents/SimpleIDE/Learn/Simple\\ Libraries/Robotics/
```

Run SimpleIDE again.  
Open up `~/catkin\_ws/src/ArloBot/PropellerCodeForArloBot/ROSInterfaceForArloBotWithDHB10.side` 
Click on the little hammer icon to just Build the code without loading it to the board.  
If it says, "Building ... done." in green highlight then everything is good!  
If it failed to build start trouble shooting or send me a note.

**5\. Learn Some More**

I suggest working through the instructions here:  
[http://learn.parallax.com/tutorials/robot/arlo/arlo-activity-board-brain](http://learn.parallax.com/tutorials/robot/arlo/arlo-activity-board-brain)

This will walk you through testing your Arlo connections and basic code to operate the the Arlo platform from the Propeller Board. Even if you are using my code to run it, it will help you to deal with problems if you understand how the basics work.

**6\. Calibration**

DHB-10: Calibration is not required for the DHB-10. There are steps on the site listed above (under Learning) for adjusting parameters, but calibration isn't required.

HB-25 Controllers: **ONLY DO THIS IF YOU HAVE THE OLD HB-25 CONTROLLERS! Otherwise skip to Step 7.**  
This step is a little complicated, so follow closely.  
This is a combination of information from  
[http://learn.parallax.com/activitybot/calibrate-your-activitybot](http://learn.parallax.com/activitybot/calibrate-your-activitybot "Activity Bot Calibration")  
and  
[http://www.parallax.com/news/2013-12-23/run-activitybot-c-code-arlo](http://www.parallax.com/news/2013-12-23/run-activitybot-c-code-arlo "Run Activitybot C Code on Arlo")  
but I've put it together here in one list of instructions.

The point of this is that you load special code into the board that, when powered on, causes the board to run a series of tests on the motors and then store the data into a special place in EEPROM. Once this is done you should never have to do it again, because no other program ever writes to this memory.

Note that this code is specially written by Parallax so that once it completes it will not run again. If you want to do the calibration again you will have to load the code into EEPROM again.  
Otherwise, once it finishes once, resetting the board will not cause it to run again.

![SimpleIDE-LoadEEPROMandRun](/img/user/attachments/SimpleIDE-LoadEEPROMandRun.png)

1\. The instructions say to put your robot in a clear area to do this. I have also just put it up on "blocks" or a sturdy box so that the wheels can run freely without moving the robot. I'm not sure which, if either, is better.  
2\. Run SimpleIDE if it isn't already running.  
3\. Open up the program ~/Documents/SimpleIDE/Learn/Examples/ActivityBot/Arlo Calibrate.c  
4\. Turn OFF the Motor switch.  
5\. Set the Activity Board switch to position 1. 
6\. Click the "Load EEPROM & Run button"  
7\. When the program is finished loading, the P26 and P27 lights will turn on. When they come on, slide Activity Board switch to 0. 
Disconnect the USB cable from the Activity Board  
8\. Turn all power off. (Both Main and Motors switches OFF.)  
9\. Set the power switch on the Activity Board to 2. (It won't come on yet because the power is off.)  
10\. Turn system power on but leave motor power off.  
11\. Press and release Activity Board's reset button.  
12\. Wait a couple seconds.  
13\. Turn on motor power and wait for it to try to do something.  
14\. Press and release Activity Board's reset again after the HB25s are convinced they are getting servo signals.  
(This last step is required only during calibration because it’s crucial to capture all encoder measurements, from the very start of the program.)  
15\. Move back to give it room to spin in place and slowly roam while it gathers wheel speed data.  
**Both** wheels should turn at some point. First it will spin in one direction, then the other. If one of the motors never comes on, you need to start over, because something went wrong.  
(Or for the wheels to just spin if you have it up on "blocks".)  
16\. Leave it alone until the P26 and P27 lights turn off (about 2 minutes). After that, calibration is complete and you can turn the power off again.

You can read more calibration trouble shooting tips here:  
[http://learn.parallax.com/activitybot/troubleshooting](http://learn.parallax.com/activitybot/troubleshooting)  
although obviously some things, like the server adjustments, do not apply.

**7\. Edit the Propeller C Code for Arlobot to fit your setup.**  
In SimpleIDE Open up ~/catkin\_ws/src/ArloBot/PropellerCodeForArloBot/ROSInterfaceForArloBotWithDHB10.side  
Now at the top there is an entire section of "#define" statements.  
You need to comment out some for items you don't have, and you need to adjust the numbers after others to indicate things like how many PING sensors you have and where they are located.  
By doing this, the code will be compiled to only include the parts you need and with setting specific to your robot.

**8\. Load Propeller C Code for Arlobot on to Propeller board.**  
The way the Propeller controller works is that if you load a program into "EEPROM" it will stay there and start any time the board is reset or power cycled. This means once the code is there you don't have to mess with it again unless you want to change something.  
If you get any of the "#define" settings wrong the first time, this could be one reason to reload it.

![SimpleIDE-LoadEEPROMandRun](/img/user/attachments/SimpleIDE-LoadEEPROMandRun.png)

Plug the USB cable back into the Activity Board and Ubuntu Laptop.  
Click the "Load EEPROM & Run button"

The board should load the code and reset.

Close SimpleIDE.  
(NOTE: If SimpleIDE is running when you try to use ROS it will mess up the communication with the Propeller Board, so be sure to close SimpleIDE before testing anything.)

**9\. Testing.**  
A good way to test your Propeller code is to run:

cd ~/catkin\_ws/src/ArloBot/scripts/
./PropellerSerialTest.sh

It will start a test engine for testing everything about your robot before trying to run ROS.

Test all output, and attempt sending twist commands directly.  
Until this works, do not expect ROS to work.

**All done!**

Remember, this is open source, so feel free to fix mistakes and make changes to the code and tell me about them! Better yet, fork the code and send me pull requests!  
Next read over README.md, or try scripts from ~/catkin\_ws/src/ArloBot/scripts/ and anything else from ROS that you want to try!  
You can go to the [ROS Turtlebot page](http://wiki.ros.org/Robots/TurtleBot/hydro "ROS Turtlebot Wiki") and read about various functions it has and attempt to make them work with your robot.

**P.S. [Prevent Propeller Activity Board from running on USB Power](Prevent%20Propeller%20Activity%20Board%20from%20running%20on%20USB%20Power.md)**   
You may want to do this if you ONLY want the the Propeller Board to run from DC power and not the USB device.
