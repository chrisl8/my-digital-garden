---
{"title":"Stairs!","created":"2015-03-25","categories":["arlobot"],"authors":["hoopy"],"tags":["Robotics","ROS","Blog"],"dg-publish":true,"permalink":"/ancient-history/2015/stairs/","dgPassFrontmatter":true}
---

*Posted: March 25, 2015*

![DalekVsStairs](/img/user/attachments/DalekVsStairs.jpg)

A couple of weeks ago it finally happened, my precious robot drive right down the stairs. Well, it drove over the threshold and tumbled down.

Amazingly the damage was limited. The front caster was bent badly and no longer functioned properly. A few bolts and screws were bent. A few of the PING/IR sensor holders were shattered.

Thanks to [Parallax](https://www.parallax.com/ "Parallax") though, my robot is already back in shape and on to new things!

**Cliff Avoidance** I've done two things to reduce the possibility of this hazard. 1. I have a home brewed "home monitor" system that emails me when a door is opened. So I added a sensor to the basement door and set it to place a file on the ArloBot's hard drive. The safty\_controller will monitor for this file and stop the robot if it exists: It would be nice, though, to build a dedicated device for this purpose, because my home monitor system is very slow. I need something that can run on battery power and send messages over Wifi.

2\. I added cliff sensors: IR sensors works better for this than PING sensors because of their very narrow focus, which is what you want when you are just watching the floor.

![Cliff Sensor](/img/user/attachments/Cliff-Sensor.jpg)

If you look carefully you can see that there is one on each side of the front PING/IR sensor. They are simply taped to the surface with double sided [3M Auto Body Molding Tape](http://www.autozone.com/sealants-glues-adhesives-and-tape/body-molding-tape/3m-1-2-in-x-15-ft-molding-tape/517047_0_0/) so that it aims down slightly.

And I have modified the code that runs on the Propeller board to stop the robot if the distance on this sensor is too great:

for (i = 5; i < 7; i++) {
if (irArray\[i\] > floorDistance) {
    safeToProceed = 0; // Prevent main thread from setting any drive\_speed
    // Stop robot if it is currently moving forward and not escaping
    if ((Escaping == 0) && ((speedLeft + speedRight) > 0)) {
        drive\_speed(0, 0);
    }
    blockedF = 1; // Use this to give the "all clear" later if it never gets set
    blockedSensor\[2\] = 1; // Pretend this is the front sensor, since it needs to back up NOW!
    pleaseEscape = 1;
    }
}

I have not done very much testing with this yet. The biggest issue is that the robot needs to be aware of the cliff soon enough to stop and reverse before falling off of the edge. A sensor on the bottom pointing straight down is very reliable, but the robot will tumble before it has time to stop. By setting the sensor at an angle this gives more time to stop.
