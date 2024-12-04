---
{"title":"Merge!","created":"2015-06-01","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2015/merge/","dgPassFrontmatter":true}
---

*Posted: June 1, 2015*

I've been working in a _dev_ branch of my [Arlobot](https://github.com/chrisl8/ArloBot) code for a long time now, and today I marged it into _Master_ so there is a lot of new code there. Hopefully it all works, but obviously I am the only one who tests it before you do.

A few of changes are: 1. I made a bunch of changes to the C code that runs on the Propeller Activity Board to try to make it more generic. You will have to answer a bunch of questions and comment out a bunch of #define lines to "customize" it for your setup, but hopefully it will be easy to do. 2. The automatic explore function should be functional now. 3. I've added some more smarts to the propeller\_node.py script to make it more robust and give myself more ability to adjsut settings while the robot is running. 4. I added my code to make use of an XV11 "Neato" vacuum cleaner scanner that I bought.

At this point I'm also working a lot in my [Metatron](https://github.com/chrisl8/Metatron) package to createa a nice GUI for interacting with the robot's functions.

My next step once this is working will be to create a new setup routine that includes installing both the ArloBot and Metatron packages and bringing up the entire package. It should work as either a monolithic "application" with a GUI or as a nifty set of convenience scripts along with access to all of the basic ROS functions that you can use on a TurtleBot. Whichever you prefer.

So head over to [https://github.com/chrisl8/ArloBot](https://github.com/chrisl8/ArloBot) and check out the commit history to see what is new and give the new code a spin if you are brave! Or wait a week or two to see if anyone else discovers a major bug! :)
