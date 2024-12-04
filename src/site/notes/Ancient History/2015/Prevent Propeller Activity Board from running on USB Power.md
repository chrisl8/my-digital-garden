---
{"title":"Prevent Propeller Activity Board from running on USB Power","created":"2015-04-14","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2015/prevent-propeller-activity-board-from-running-on-usb-power/","dgPassFrontmatter":true}
---

*Posted: April 14, 2015*

If you have an [Arlo Power Distribution Board](https://www.parallax.com/product/28996 "Arlo Power Distribution Board"), and you frequently leave your [Activity Board](https://www.parallax.com/product/32910 "Activity Board") plugged into a notebook computer when you turn off the Arlo Power Distribution Board, you may have noticed that the Activity Board stays on. Furthermore, anything connected to the 5 volt supply on the Arlo Power Distribution Board stays on also. The Activity Board is getting power from the USB port on the computer, and then it is passing this 5 volts on to other devices via the barrel connector.

Parallax has kindly provided instructions on how to prevent the Activity Board from drawing any power from the USB Port: [https://forums.parallax.com/discussion/160774/reverse-power-flow-in-arlo-power-supply](https://forums.parallax.com/discussion/160774/reverse-power-flow-in-arlo-power-supply)

I performed **both** steps 7 and 8 to ensure that mine would not run from USB power under any circumstances, because I never want it to do that on my robot.

Now your Activity Board will turn off when you turn off the Arlo Power Distribution Board and everything else will shut off too!

This also opens up the possibility to power cycle the Activity Board with the [USB Relay Board](http://www.amazon.com/SainSmart-Eight-Channel-Relay-Automation/dp/B0093Y89DE/ref=sr_1_1?ie=UTF8&qid=1429042225&sr=8-1&keywords=usb+relay). I have not done this yet, because I knew it was pointless as long as the Activity Board would continue to draw power from the USB port. I might try it now though, because sometimes I think a power cycle would be the most reliable way to force a reset on the Activity Board. All it would take is running the 6.5 volt wire through one of the relays before going to the Activity Board.
