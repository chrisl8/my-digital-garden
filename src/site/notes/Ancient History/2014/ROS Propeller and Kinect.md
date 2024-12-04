---
{"title":"Ros, Propeller and Kinect!","created":"2014-07-17","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2014/ros-propeller-and-kinect/","dgPassFrontmatter":true}
---

*Posted: July 17, 2014*

I have been very busy over the past few months building up a robot to make use of the [Robot Operating System (ROS)](http://www.ros.org/ "Robot Operating System")

[Willow Garage](https://www.willowgarage.com/ "Willow Garage") has their own ready to go robot called the [TurtleBot](https://www.willowgarage.com/turtlebot "TurtleBot 2") which is a very good system, and has amazing abilities right out of the box.

However I've already been planning my robot version for a while and ROS is more of an addon, albeit a huge one, then a starting point. While the TurtleBot has a lot of features that I may never be able to come up with myself, it is missing a couple of key ones:

1. It has a very limited ground clearance.
2. The payload is quite limited.

What I've been looking at is the Arlo Robot from Parallax: [http://www.parallax.com/product/arlo-robotic-platform-system](http://www.parallax.com/product/arlo-robotic-platform-system "Arlo Robot platform from Parallax")

This is by no means a "pull it out of the box and go" platform, but it is well within my skills. No designing circuits, no laser cutting, no hacking together of bits of metal and plywood. It can be built by anyone who can put together a radio controlled car kit, and their site is basically designed around [teaching kids](http://learn.parallax.com/ "Parallax Learn") how to program their controller board, so the learning curve is well assisted.

Fortunately the Arlo Robot is also similar in shape and layout to the TurtleBot. Once I built code for the [Propeller](http://www.parallax.com/microcontrollers/microcontrollers-overview "Propeller Chip") based [Activity Board](http://www.parallax.com/product/32910 "Propeller Activity Board") to talk to ROS, I can actually run a lot of the ROS TurtleBot code with very little modification!

Here is a list of my progress so far:

1. I have written code to communicate between the Propeller based Activity Board and ROS, sending odometry information and accepting twist messages from ROS.
2. I have adapted the 3D view, robot model and teleop code from the ROS TurtleBot to run on my robot.
3. I have built a basic URDF model of the Arlo robot.

I am doing all of this on a little [ActivityBot](http://www.parallax.com/product/32500 "Parallax ActivityBot"), because it uses the exact same controller as the ArloBot. Right now I am just waiting on parts from Parallax to get my ArloBot together so that I can start running ROS with it.

I have not made SLAM or "gmapping" work well yet because the odometry from the ActivityBot is very poor due to the fact that its little rubber clad wheels slip very easily and very unevenly on all floor surfaces. I expect the ArloBot to have much less wheel slip. I will also be experimenting with adding a gyro to the Propeller Activity Board to assist in verifying rotation angles.

Since a photo is worth a thousand words, here is a picture of where I'm at at the moment:

![Robot Progress July 17, 2014](/img/user/attachments/robotprogress.png)

Here you can see my rudimentary ArloBot URDF with a depth registered 3D image from the ASUS Xtion Live and the simulated red laser scan line. Also notice the small line of white dots in front of the robot. That is a simulated LaserScan built from the PING sensor on the front of the ActivityBot. I plan to place PING (Ultrasonic) and InfraRed sensors around the ArloBot and use simulated LaserScans from them to help the robot navigate around low or close obstacles that the 3D Camera misses.

I have a lot of documentation on my process and my code is all online, so if anyone is interested in more about this please let me know and I will post some more background as well as on going work.
