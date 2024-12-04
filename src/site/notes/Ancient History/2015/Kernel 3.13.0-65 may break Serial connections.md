---
{"title":"Kernel 3.13.0-65 may break Serial connections!","created":"2015-09-30","authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2015/kernel-3-13-0-65-may-break-serial-connections/","dgPassFrontmatter":true}
---

*Posted: September 30, 2015*

Yesterday, after updating to the linux-image-3.13.0-65-generic 3.13.0-65 Kernel on Lubuntu 14.04.3 LTS using the normal Ubuntu update/upgrade two different programs that rely on PySerial quit working. miniterm.py and my ROS (Robot Operating System) based Python node quit working.

 

$ miniterm.py /dev/ttyUSB0 115200
--- Miniterm on /dev/ttyUSB0: 115200,8,N,1 ---
--- Quit: Ctrl+\] | Menu: Ctrl+T | Help: Ctrl+T followed by Ctrl+H ---

--- exit ---
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 810, in \_\_bootstrap\_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 763, in run
    self.\_\_target(\*self.\_\_args, \*\*self.\_\_kwargs)
  File "/usr/bin/miniterm.py", line 220, in reader
    data = character(self.serial.read(1))
  File "/usr/lib/python2.7/dist-packages/serial/serialposix.py", line 460, in read
    raise SerialException('device reports readiness to read but returned no data (device disconnected?)')
SerialException: device reports readiness to read but returned no data (device disconnected?)

To resolve your issue temporarily reboot, and at the "GNU GRUB" menu select "Advanced options for Ubuntu" and then move down to select the Ubuntu, with Linux 3.13.0-63-generic kernel option. (NOT the recovery mode one) and it should boot into the old kernel and work fine again.Reverting to the 3.13.0-63 kernel allows miniterm.py and other Python Serial based programs to work normally.

**To fix the issue permanently:** Remove the new kernel with:

sudo apt-get remove linux-image-3.13.0-65-generic

and reboot, which will remove the new kernel and remove it from GRUB.

There is a bug report open for this: [https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1500860](https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1500860) I also opened my own, but it is probably a duplicate of the above [https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1501345](https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1501345)

Hopefully the next kernel patch won't break it again.
