---
{"title":"ROS Kinetic Setup","created":"2014-11-03","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2014/ros-kinetic-setup/","dgPassFrontmatter":true}
---

*Posted: November 3, 2014*

**WARNING: OLD VERSION!**  
This is an old version. You should use [ROS Noetic Setup](ROS%20Noetic%20Setup.md)

In the last article I explained how to set up an Ubuntu laptop for use by ROS. Here I'm posting my notes about how to get ROS Kinetic up and running on that laptop.

**There is now a script to install everything.**  
Just run:

```
bash <(wget -qO- --no-cache https://raw.githubusercontent.com/chrisl8/ArloBot/new-serial-interface/setup-kinetic.sh)
```

and you are done!

To update your code just run the same script again and it will pull down and compile anything new without erasing custom settings.

NEXT!  
**Next we’ll want set up [Propeller Code for Arlobot (SimpleIDE Version)](Propeller%20Code%20for%20Arlobot%20(SimpleIDE%20Version).md)
