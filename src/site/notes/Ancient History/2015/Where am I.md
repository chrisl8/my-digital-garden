---
{"title":"Where am I?","created":"2015-08-20","authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2015/where-am-i/","dgPassFrontmatter":true}
---

*Posted: August 20, 2015*

Someone asked where I've been. What have TwoFlower and I been doing?

I have been quiet here because the robot has gone from a fever of building to slow steady background work. My focus right now is to build an internal "behavior" system using [Behavior3JS](http://behavior3js.guineashots.com/) to allow the robot to "act" more independently.

The first goal is simply to have it intelligently go from "power on" to freely moving about the room. This may sound simple, but there are a lot of start-up tasks that need to be coded properly so that things are safe and sane. Then the robot needs to know where he is, load a map for that room, know where he is in that room if point 0 on the map doesn't happen to be it, know if any doors in the room are open which might lead to dangerous stairs, and unplug himself.

My github repo kind of shows my work days and progress [https://github.com/chrisl8/Metatron/commits/master](https://github.com/chrisl8/Metatron/commits/master), but I realize it is also cluttered because I commit too often.

So here is a brief timeline of what I've been laboring away at:

June 16th - This is when I built the web based control panel that runs both on board and can be remotely accessed. This lets me control important parameters of the robot remotely and get him started remotely without having to run lots of scripts:

![ArloBotControlPanel](/img/user/attachments/ArloBotControlPanel.png)

June 17th - I built a setup script to allow you to install everything from one command. This is documented on the front of my [Arlobot](https://github.com/chrisl8/ArloBot) repository now in the readme.

July 2nd - I added [roslibjs](https://github.com/RobotWebTools/roslibjs) to my Node based control panel so that ROS functions can be directly polled and controlled.

July 5th - I added the ability to set "waypoints" using the web interface. This means you can drive the robot to a position on the map, set a waypoint, and then in the future you can tell it to go to that waypoint again and it will return to the same spot on the map. Now places like "Kitchen" and "LivingRoom" can easily be set and recalled.

July 7th - Added QR code reading. Now the robot can use a QR code taped to the wall to determine what room it is in as soon as it is started and automatically load the correct map for the room without any human intervention.

August 17th - Added the function for the robot to use a waypoint called "initial", if found for the map, to set its initial "2D pose estimate" so if your normal starting point isn't the same as point 0 on the map, the robot can automatically localize itself on startup.

Somewhere in there I also tweaked the "stop if a door is open" code and I installed a [Moteino](http://lowpowerlab.com/moteino/) based door monitor on my basement door to alert the robot.

![moteino](/img/user/attachments/moteino.jpg)

Next I am working on the self unplugging routine. This isn't super fancy. I just anchor the cord to the wall and have the robot back up, but once this works the robot can start up and go without human interaction!

So that is what I've been doing! :)

It excites me a lot when someone reaches out and asks what I'm up to and why no recent posts. So thank you!
