---
{"title":"ROS &lt;remap&gt; tag","created":"2015-02-27","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2015/ros-remap-tag/","dgPassFrontmatter":true}
---

*Posted: February 27, 2015*

This shouldn't be rocket science, but up until just this moment I never comprehended the <remap> tag.

However, due to a problem I was having I had the opportunity to track it down, in action, and also to see the result.

First, this is documented, but the documentation never made sense to me: [http://wiki.ros.org/roslaunch/XML/remap](http://wiki.ros.org/roslaunch/XML/remap)

or for more confusion: [http://wiki.ros.org/Remapping%20Arguments](http://wiki.ros.org/Remapping%20Arguments)

So here is my explanation to myself:

If you look inside of my [ArloBot](https://github.com/chrisl8/ArloBot) [propellerbot\_node.py](https://github.com/chrisl8/ArloBot/blob/master/src/arlobot/arlobot_bringup/scripts/propellerbot_node.py) you will see that it listens to the topic cmd\_vel:

`rospy.Subscriber("cmd_vel", Twist, self._handle_velocity_command)`

However, if you start up my ArloBot:

`roslaunch arlobot_bringup minimal.launch --screen`

and start driving it around with TeleOp:

`roslaunch arlobot_teleop keyboard_teleop.launch`

You will see NO cmd\_vel topic!

chrisl8@ArloBot (master \*) scripts $ rostopic list
/arlo\_status
/arlobot/pirState
/arlobot\_safety/safetyStatus
/arlobot\_usbrelay/usbRelayStatus
/cmd\_vel\_mux/active
/cmd\_vel\_mux/input/navi
/cmd\_vel\_mux/input/safety\_controller
/cmd\_vel\_mux/input/teleop
/cmd\_vel\_mux/input/web
/cmd\_vel\_mux/parameter\_descriptions
/cmd\_vel\_mux/parameter\_updates
/infrared\_scan
/joint\_states
/mobile\_base/commands/velocity
/mobile\_base\_nodelet\_manager/bond
/odom
/rosout
/rosout\_agg
/serial
/tf
/ultrasonic\_scan

In ROS there is so much going on that it is easy to chalk things up to "magic", but when you actually write the Python code to listen to cmd\_vel, and there is no cmd\_vel topic, no amount of "magic" suffices. Obviously something is wrong!

The solution is <remap>, and the lesson is that this tag works on an individual node at the time we run it!

We called propeller\_node.py with minimal.launch, and it includes the file mobile\_base.launch.xml:

<include file="$(find arlobot\_bringup)/launch/mobile\_base.launch.xml" />

and inside of this file is the "magic":

  <node pkg="arlobot\_bringup" type="propellerbot\_node.py" name="arlobot" respawn="true" args="--respawnable">
    <param name="bonus" value="false" />
    <param name="update\_rate" value="30.0" />
    <remap from="cmd\_vel" to="mobile\_base/commands/velocity" />
    <remap from="arlobot/sensor\_state" to="mobile\_base/sensors/core" />
    <remap from="imu/data" to="mobile\_base/sensors/imu\_data" />
    <remap from="imu/raw" to="mobile\_base/sensors/imu\_data\_raw" />
    <rosparam file="$(find arlobot\_bringup)/param/arlobot.yaml" command="load" />
  </node>

The exciting line is this one:

`<remap from="cmd_vel" to="mobile_base/commands/velocity" />`

This says that when the node we are calling (propellerbot\_node.py) tries to subscribe to "cmd\_vel" give it "mobile\_base/commands/velocity" instead!

Mystery solved, because that topic does exist!

Furthermore, if you run or create a node that sends data on the "cmd\_vel" topic, nobody is going to listen to it!

I don't know why these remaps were so confusing to me before. Probably because a lot of them are only used in the TurtleBot code that I borrowed from. Only when I had a clear situation where a third party node was talking on cmd\_vel and nothing was happening did I realize that there IS NO cmd\_vel topic in my normal setup, and yet it worked.

Question 2:

If I have a launch file that I want to start, and I know the node it starts will broadcast to a topic I don't listen to, either directly or due to remapping, what can I do about this?

Based on this now less confusing documentation of argument remapping: [http://wiki.ros.org/Remapping%20Arguments](http://wiki.ros.org/Remapping%20Arguments)

You can also use remap when you run a node directly, so that this:

(This is based on a command from the great [ROS by Example INDIGO](http://www.lulu.com/shop/r-patrick-goebel/ros-by-example-indigo-volume-1/ebook/product-22015937.html) book that you really should buy!)

`rosrun rbx1_nav calibrate_linear.py`

becomes:

`rosrun rbx1_nav calibrate_linear.py cmd_vel:=mobile_base/commands/velocity`

Because I know from experience (run the command and then run "rostopic list" to get that same experience) that this node broadcasts on "cmd\_vel", and from my previous discussion based on launch files and the output of "rostopic list" that my robot's controller node listens on mobile\_base/sensors/core
