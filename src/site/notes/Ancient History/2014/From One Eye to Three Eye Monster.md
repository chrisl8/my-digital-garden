---
{"title":"From One Eye to Three Eye Monster","created":"2014-02-19","authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2014/from-one-eye-to-three-eye-monster/","dgPassFrontmatter":true}
---

*Posted: February 19, 2014*

![Three Eyed Monster](/img/user/attachments/3eyeMedium.jpg)

Thanks to [BrickLink](http://www.bricklink.com/ "BrickLink") I found I could buy used UltraSonic sensors for less than $10 each! So I bought two, and now my little friend shouldn't run into walls as much.

He should also be able to follow a wall on one side while avoiding obstacles ahead.

I tried putting all three up top, like the [picture](attachments/HoopyTwitterProfile.png) in my first post, but besides getting top heavy, I found I was unable to see a lot of obstacles. Putting all three down low makes them far more steady, makes it less top heavy, and allows me to see lower obstacles.

Because the sensors are not "adjustable" and only provide a basic "distance to nearest object" response, their position on the vehicle determines what you see and what you miss. So the lower I mount them, the lower of an object I can see. Too low and they see the ground, too high and they miss things. Just right and they see what I cannot driver over!

Now the fun part is programming. [leJOS](http://www.lejos.org/ "leJOS") provides great functions for dealing with UltraSonic sensors, but there is a catch with multiple sensors: The way they work is that they send out a ping and listen for the sound to bounce back. If two are going at once, they cannot tell if the return sound is their own or another one.

By default they run "continuously" and you just poll a sensor for the latest reading, but with more than one, you need to make sure only one sends a ping at a time. So now I get to write code to cycle them:
 - Turn on sensor 1, ping, record distance measured, turn off.
 - Turn on sensor 2, ping, record distance measured, turn off.
 - Turn on sensor 3, ping, record distance measured, turn off. Repeat.

Then I have to do something with all of this data, but that comes later . . .
