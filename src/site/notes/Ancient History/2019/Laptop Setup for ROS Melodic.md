---
{"title":"Laptop Setup for ROS Melodic","created":"2019-11-07","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2019/laptop-setup-for-ros-melodic/","dgPassFrontmatter":true}
---

*Posted: November 7, 2019*

**WARNING: OLD VERSION!  
You should use the [Laptop Setup for ROS Noetic](Laptop%20Setup%20for%20ROS%20Noetic.md) now.**

Part of the ArloBot setup is to have a laptop riding on board the robot to run ROS. This article is a quick set of instructions for setting up that Laptop.

**My Laptop:**  
I am currently using a beat-up Dell XPS 15 9530 that my brother-in-law took to the desert and back. It has a nice fast CPU and lots of memory although the battery life isn't great.  
I previously used a well loved HP EliteBook 2760p from Ebay.

U**buntu 18.04 Desktop 64 bit:**  
ROS Melodic is built for [Ubuntu LTS 18.04 Desktop](http://www.ubuntu.com/download/desktop). It is the "Long Term Support" (LTS) version, so you can download and use it for several years without having to upgrade to the next version. This gives the [ROS](http://www.ros.org/) development community some stability in their target OS.

You can also use one of the Ubuntu derivatives such as Lubuntu or Xubuntu if you are highly familiar with them, as long as they use the same package repository as Ubuntu.

Just remember that it must be an Ubuntu Desktop variant of version **18.04 LTS** (the .01, .02, .03 on the end is fine). Other Linux distributions will not work, nor will newer versions of Ubuntu.

**Download** Ubuntu Desktop 18.04 LTS 64bit ISO (ubuntu-18.04.3-desktop-amd64.iso) from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)  
My laptop has no DVD drive, so I have to use a USB "flash drive" to install.

If you are on Windows, use the instructions here to create a bootable USB flash drive if you need to:  
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)  
If you are on Linux, I like to use [https://www.balena.io/etcher/](https://www.balena.io/etcher/) to put the ISO onto my USB flash drive.

**In the BIOS** I suggest that you:  
\* Turn off Secure Boot  
\* Turn off "Fast Boot"  
\* Enable USB boot if it isn't already to get it to show up in the boot options.

I recommend that you do **NOT** plug the laptop into Ethernet during install. This way the Ubuntu setup will ask you to configure WiFi during setup, proving it works and getting it preconfigured during install.

Boot from the USB stick or DVD you created with the Ubuntu (or Lubuntu, Xbuntu, etc.) ISO.

Install Ubuntu

Connect to WiFi

**Minimal** installation - We don't need Libreoffice, and anything we do need, we can add later.

CHECK: Download updates while installing

**I** like to include third-party drivers. You don't have to, but know that my install is using them, so if you run into strange WiFi or Video issues, this could be the cause if you didn't include 3rd party drivers.

_Continue_

Pick your Installation Type:  
Really, anything here will work. You can dual boot with Windows or another Ubuntu version, or erase the disk.  
Personally I always pick the "erase disk" option because nothing else runs on the system I use for my robot.

_If you are asked about encryption or LVM_:  
I recommend **not** using encryption,  
and you do **not need** LVM either.

_Continue_

Pick your time zone.

Your Name: _Chris L8_ **(replace with the name you want)**  
Your computer's name: _ArloBot_ **(Or pick something else)**  
Pick a username: _chrisl8_ **(Replace with the user ID you want for Ubuntu)**  
CHECK: Log in automatically - _I prefer this, but you don't have to._

_Continue_

**Once you boot into the Ubuntu Desktop:**

On first boot a window will come up asking for some options.  
I do not set up "Live Update", nor do I have my install send data to Canonical. Basically set up as little as possible.

Shortly after the first boot the Software Updater will ask to install updates. Go ahead and install all updates and reboot if asked to. It isn't required, but saves time later and sometimes trying to update everything at the same time as installing ROS causes issues.

**After your first set of updates and reboots:**

Once Ubuntu starts click on the "Show Applications" button in the bottom left and type "terminal" and run Terminal:

Right click on the icon on the left and select "Add to Favorites" to keep it there for easy use in the future.

You can also drag it up higher on the dock after you lock it,

and you can right click it and run a "New Terminal" when you need another one.

**Install the SSH server:**

sudo apt install openssh-server

_Now you can use ssh from Linux or [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) where you can cut/paste._  
If you are not familiar with how to use SSH to connect to Linux machines, search the Internet for "ssh putty tutorial". I thought this one looked pretty good: [SSH Tutorial for Windows](http://support.suso.com/supki/SSH_Tutorial_for_Windows)

**Enable Remote Control of GUI Desktop:**  
The entire idea of a robot is to be remote, so it will help a lot to be able to control it from your desktop.  
VNC works well. If your normal computer is running Windows use [TightVNC](http://www.tightvnc.com/).  
If you are on Ubuntu you can use Remmina. Click on the "Search Desktop" button, type "remmina".

**Install VINO for remote desktop on the robot:**

```
sudo apt install vino
```

**VNC Setup on Ubuntu:**  
From "Show Applications" type "settings" to search for it.  
Find and click on "Settings"  
Find and click on "Sharing" on the left.  
If the switch in the upper right is OFF turn it ON.  
Select "Screen Sharing".  
(IF "Screen Sharing" doesn't exist on the screen, open a terminal window and run "sudo apt install vino" and then try again)  
Turn it on and set a password.  
The official instructions are here: [https://help.ubuntu.com/stable/ubuntu-help/sharing-desktop.html.en](https://help.ubuntu.com/stable/ubuntu-help/sharing-desktop.html.en)

**Customize Ubuntu Desktop:**  
These are all a matter of personal preference, but I find this to be the best way to set things up for myself.

Settings->  
Power:  
CHECK: Dim screen to save power  
Turn screen off when inactive for: 5 minutes **(or set as you like)**  
Automatic suspend: Off **(or set as you like)**  
Suspend when inactive for: Don't Suspend     Don't suspend  
When power is critically low: Power off  
When the lid is closed: Do Nothing     Do nothing  
Privacy:  
Screen Lock: Off  
UNCHECK: Require my password when waking from suspend  
Background:  
Change "Background" and "Lock Screen" to "Colors"  
Pick the solid black color  
Search:  
Off

**Byobu:** (I use tmux myself, but if you are new to Linux, this is a good option)  
When you run ROS nodes on the laptop via SSH they will be in your session. If your session disconnects it will stop ROS.

To allow your session to continue in the case of an accidental or even purposeful disconnect you can use a program called tmux (or screen) that lets you leave running "sessions" open. byobu is a front end to tmux that makes it pretty and easier to use.

sudo apt install byobu

byobu-enable This will cause byobu to automaticlaly start when you connect via SSH.

Log off and back on,  
The first time you press ctrl-a it will ask if you want this to go to work with Emacs or Screen, pick Screen.  
F1, Toggle Status, add/remove what you want. I like to add the battery level.

**Disable lid close detection:** If you want to run your laptop on the robot with the lid closed, you may need to do this, because when you reboot or try to shut down while the lid is closed and the laptop is on battery power, as soon as XWindows shuts down the computer goes to sleep before it even shuts down!  
This leaves the laptop in a limbo where it sleeps until the battery dies with no hope of connecting to it until you open the lid and let it finish shutting down!  
**_I found two solutions. I am using the first option, which works for me, but if Option 1 doesn't work try Option 2._**  
Option 1. Set "IgnoreLid=true" in /etc/UPower/UPower.conf  
sudo vi /etc/UPower/UPower.conf  
CHANGE:  
IgnoreLid=false  
TO:  
IgnoreLid=true

Option 2. Set LidSwitchIgnoreInhibited=no and HandleLidSwitch=ignore in /etc/systemd/logind.conf:  
sudo vi /etc/systemd/logind.conf  
CHANGE:  
#LidSwitchIgnoreInhibited=yes  
TO:  
LidSwitchIgnoreInhibited=no  
AND CHANGE:  
#HandleLidSwitch=suspend  
TO:  
HandleLidSwitch=ignore  
Reboot to make these changes take affect.

NEXT!  
**Next you will want to do the [ROS Melodic Setup](ROS%20Melodic%20Setup.md)**
