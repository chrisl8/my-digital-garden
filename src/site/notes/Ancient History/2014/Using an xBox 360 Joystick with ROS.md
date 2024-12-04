---
{"title":"Using an xBox 360 Joystick with ROS","created":"2014-11-06","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2014/using-an-x-box-360-joystick-with-ros/","dgPassFrontmatter":true}
---

*Posted: November 6, 2014*

https://www.youtube.com/watch?v=pzgZBdiqDHo

To use an xBox controller with a PC (Windows or Linux) you need a receiver, which are fortunately easily obtained.  
I purchased this "[Wireless PC USB Gaming Receiver for Xbox 360](http://www.amazon.com/Wireless-Pc-Gaming-Receiver-Xbox-xbox360/dp/B0076HD2W8/ref=sr_1_1?ie=UTF8&qid=1415203239&sr=8-1&keywords=xbox+controller+pc+usb "Wireless Pc Usb Gaming Receiver for Xbox 360")" from Amazon for under $10.

Note: I'm not sure if there is any way to "disassociate" an xBox controller from your xBox. You just connect it to a new device. I found that if I turned on the controller in another room it was far enough away that the xBox did not power on. If the xBox keeps turning on and grabbing your controller just unplug it from the wall so it has no power. Once your associate the controller with the PC adapter it shouldn't turn on the xBox anymore.  
Reconnecting it to the xBox should be as easy, just remember if you want to go back and forth you'll have to keep doing this.

ROS already has a page about [Configuring and Using a Linux-Supported Joystick with ROS](http://wiki.ros.org/joy/Tutorials/ConfiguringALinuxJoystick#Configuring_the_Joystick "Configuring and Using a Linux-Supported Joystick with ROS"). I will just be adding my findings specific for the xBox 360 and my ArloBot.

Before I plug in the adaptor my Ubuntu machine already shows one "js" device:

chrisl8@ArloBot:~$ ls /dev/input/js\*
/dev/input/js0

This appears to be some sort of accelerometer, possible built into the HP Elitebook laptop?!

chrisl8@ArloBot:~$ sudo jstest /dev/input/js0
Driver version is 2.1.0.
Joystick (ST LIS3LV02DL Accelerometer) has 3 axes (X, Y, Z)
and 0 buttons ().
Testing ... (interrupt to exit)
Axes:  0:     0  1:  -521  2: 16066

That is not what I am after now, but it sure seems like I should look into it in the future! Maybe your laptop has one too?!

When I plug the USB adapter for the xBox joystick into my laptop I get **four** new "js" devices.

chrisl8@ArloBot:~$ ls /dev/input/js\*
/dev/input/js0  /dev/input/js1  /dev/input/js2  /dev/input/js3  /dev/input/js4

I guess since the xBox standard is to support 4 controllers, the USB PC adapter provides 4 devices right up front.

Press the button on the USB adapter and it starts flashing.  
Press and hold the small round button on the back of the xBox controller that looks like "O)))" until the lights on top of the controller start to "spin".

The light on the USB adapter will stop flashing almost immediatly and the lights on the controller will stop spinning and start flashing all together.  
This part is confusing, because when the controller is connected to the xBox you get one quadrant lit up to show which controller it is. Instead on the PC I just get all 4 lights flashing at me, which is kind of annoying.

However, if you run sudo jstest /dev/input/js1 you will indeed see that Ubuntu sees the controller and it is the first one!

chrisl8@ArloBot:~$ sudo jstest /dev/input/js1
Driver version is 2.1.0.
Joystick (Xbox 360 Wireless Receiver (XBOX)) has 6 axes (X, Y, Z, Rx, Ry, Rz)
and 15 buttons (BtnX, BtnY, BtnTL, BtnTR, BtnTR2, BtnSelect, BtnThumbL, BtnThumbR, ?, ?, ?, (null), (null), (null), (null)).
Testing ... (interrupt to exit)
Axes:  0: -5086  1:     0  2:-32767  3: -1291  4:  1066  5:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off

If your screen scrolls instead of updating the line of input in place try resizing your terminal window.

Clearly we have a LOT of input options here and a lot of cool buttons for doing all sorts of stuff!

It is kind of fun to play with and learn about how the controller works this way! :)

So now we carry on with the [ROS instructions](http://wiki.ros.org/joy/Tutorials/ConfiguringALinuxJoystick#Configuring_the_Joystick "Configuring Joystick in ROS"):

Make sure the js1 device is read/writeable by everyone:

chrisl8@ArloBot:~$ ls -la /dev/input/js1
crw-rw-r--+ 1 root root 13, 1 Nov  5 15:48 /dev/input/js1
chrisl8@ArloBot:~$ sudo chmod a+rw /dev/input/js1
chrisl8@ArloBot:~$ ls -la /dev/input/js1
crw-rw-rw-+ 1 root root 13, 1 Nov  5 15:48 /dev/input/js1

You will need to have ROS running at this point, so if you don't, start it.  
If you don't know what I mean, just open another terminal window and run roscore so it can be running over there while you carry on over here.

Now make sure your xBox controller is still on and run:

rosparam set joy\_node/dev "/dev/input/js1"
rosrun joy joy\_node

Now start **another** terminal (yeah, ROS is big on having dozens of terminals open to test things) and run:

rostopic echo joy

It should be quiet as long as you do nothing, and then it should spit out lines like this if you push any button or move any stick:

\---
header:
  seq: 429
  stamp:
    secs: 1415227355
    nsecs: 833352850
  frame\_id: ''
axes: \[0.19235174357891083, -0.0, 1.0, -0.04268254339694977, -0.048208002001047134, 1.0\]
buttons: \[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0\]
---

A button push will give one entry for each up and down.  
Moving an analog stick or button will send a lot of them as a stream of the analog output!

Now we know that ROS can see the input from your xBox controller!!!

One nice thing is that the ROS joy node can deal with the controller shutting down. With just jstest it would quit if the controller shut off or went out of range, but the joy node will keep attempting to reconnect, which you can even see in the output:

chrisl8@ArloBot:~/arlobot? rosrun joy joy\_node
\[ INFO\] \[1415227328.714727550\]: Opened joystick: /dev/input/js1. deadzone\_: 0.050000.
\[ERROR\] \[1415227389.322316326\]: Connection to joystick device lost unexpectedly. Will reopen.
\[ERROR\] \[1415227389.322740820\]: Couldn't open joystick /dev/input/js1. Will retry every second.
\[ INFO\] \[1415227390.342425225\]: Opened joystick: /dev/input/js1. deadzone\_: 0.050000.

**NEXT: Use the xBox controller and joy node to control ArloBot!**

So now how do we make use of this in ArloBot?  
Certainly we could write custom code and/or modify code to make use of the amazing arrow of inputs, but ROS already has code for this. Later I may augment this to make use of more of the buttons, but for now I'm going to try to just use what is included in ROS with as little modification as possible.

Don't follow on with the ROS page we were at before, that was just to make sure we could see the controller in Linux and show us how to debug.  
Now we want to find a node that we can use with ArloBot with the least fuss.

The easiest way to do this is to just launch ArloBot's minimal bringup package and then launch turtlebot's teleop:

roslaunch arlobot\_bringup minimal.launch --screen

rosparam set /joystick/dev "/dev/input/js1"
roslaunch turtlebot\_teleop xbox360\_teleop.launch --screen

The way this works is that it ONLY sends commands to the robot while the left "shoulder" button is held down. It is labeled "LB". Hold that down and move the left stick and the robot should respond!  
If things get out of hand just let go of the "LB" button and all zeroes will be sent again to make it stop.

And that's it! It should work.

I will probably do some tweaking and customizing of my own joystick teleop code and include it in the ArloBot github repository soon. Until then though, the TurtleBot code is working fine.
