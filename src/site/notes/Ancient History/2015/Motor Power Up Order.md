---
{"title":"Motor Power Up Order","created":"2015-10-11","authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2015/motor-power-up-order/","dgPassFrontmatter":true}
---

*Posted: October 11, 2015*

So you got your robot built, installed everything, and the calibration worked, but now that you actually want to run the robot it does nothing.

The first thing is to turn it on and go use the \`~/catkin\_ws/src/Metatron/scripts/direct2PropSerialTest.sh\` script along with the recommended commands from \`~/catkin\_ws/src/Metatron/scripts/direct2PropSerialTestLines.txt\` to observe and test how everything works without ROS. However, most people seem to either be doing this already, or be well past it, because you guys are really smart! :)

There is a hidden problem though. It is discussed in the calibration instructions, so I was assuming everyone knew about it, but I now realize it isn't well explained.

Three separate people have contacted me with this issue, so I want to post it here on the blog. The motor controllers have a strange quirk. Their "normal" mode does not work with the Propeller board! However, within the first few seconds after turning them on they listen for a certain kind of signal. If they get it, they flip to a mode that **does** work with the Propeller.

What does this mean? If you turn on the motors, then start everything up, the robot won't do anything.

The solution: You have to wait until the Propeller board is fully running, after the first arlo\_drive command has been sent to turn on the motors. If you have PING sensors installed, you can know when it is time to turn the motors on by when the PING sensors start flashing. The main thing is just to make sure the Propeller board is "initialized" before you turn on the motors. That means after the ROS arlobot program is already started, or after you sent the "i   0" to it via the \`direct2PropSerialTest.sh\` command.

Another solution? Get a [USB Controlled Relay](http://www.amazon.com/SainSmart-Eight-Channel-Relay-Automation/dp/B0093Y89DE/) and wire it between the motor outputs on the Arlo Power Distribution board and the motor controllers. This way the code will actually turn on the motors at the right time. This is how mine is set up, and why I forget about this problem.
