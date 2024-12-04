---
{"title":"Parallax SimpleIDE on Raspberry Pi with VNC and SSH","created":"2014-09-04","categories":["arlobot"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2014/parallax-simple-ide-on-raspberry-pi-with-vnc-and-ssh/","dgPassFrontmatter":true}
---

*Posted: September 4, 2014*

This is my setup log for my second Raspberry Pi. It is a little older, but I think some might find the walk through useful. This could be used to create a robot that is easy to program and control remotely via VNC and SSH. This is more of a "log" of my work than instructions, so **a lot of it is cut and paste from the sources listed**. Please let me know if you run into questions or problems and I will make updates.

My goal with this one is to set it up to work over WiFi

GUI available via VNC

and run the Propeller SimpleIDE to control the Propeller board

**Getting started:**

- Put it in the case (if you bought one).
- Plug in Ethernet
- Monitor via HDMI (You can use any TV in the house!)
- Keyboard (This is only temporary so just steal one from your kids!)
- Mouse (This is only temporary so just steal one from your kids!)
- Hold off on the power.

* * *
 **Following Propeller's instructions:**

[http://learn.parallax.com/propeller-c-set-simpleide/raspberrypi](http://learn.parallax.com/propeller-c-set-simpleide/raspberrypi)

_(The following is cut and pasted from the above site, it is NOT my work!)_

Install th?e Operating System

- Find an available desktop or laptop computer with an SD card reader/writer.
- Insert the SD card for your Raspberry Pi into the computer’s SD card reader/writer.
- Point a web browser at the Raspberry Pi downloads site ([http://www.raspberrypi.org/downloads](http://www.raspberrypi.org/downloads)).
- Download, install, and run the SD Card Association’s formatting tool from the link provided at the Raspberry Pi downloads page.
- Use this software to format the SD card properly for use with the Raspberry Pi.  Make sure to click the _Option_ button, select "Full (Erase)" from the _Format Type:_ field and select "On" from the _Format Size Adjustment_ field, then click the _OK_ and _Format_ buttons.

![](/img/user/attachments/Image.png)

- Go back to the Raspberry Pi downloads site to get the OS image.

**For the best experience, use the New Out Of Box Software (NOOBS) to install the operating system image.** There are many Linux distributions for Raspberry Pi, but NOOBS makes it easy to try them all from a single SD image.

- Download the NOOBS image and extract its contents onto the SD card.
- Eject the SD card from your computer and insert it into the Raspberry Pi.
- Plug in the USB hub’s power supply.
- Plug in the Micro-USB power supply to power up the Raspberry Pi.
- After a few moments, NOOBS will boot and present you with a simple OS Installation menu.
- Set Language to English (US)
- **Select the "Raspbian" operating system** and then click _Install OS_. NOOBS will install Raspbian onto your SD card and will then reboot.

**Keep default settings but set GUI desktop to start automatically.** At the end of the first reboot, the Raspberry Pi Software Configuration Tool will appear. All the defaults are fine, except we recommend setting the GUI desktop to automatically start up after boot.

- Default User name/Password is pi/raspberry
- On the Raspberry Pi Software Configuration Tool, move the highlight down to the "Enable Boot to Desktop/Scratch" item and press Enter to select.
- On the "Choose boot option" prompt, move the highlight to "Desktop log in as user 'pi' at the graphical desktop" and press Enter to select.
- Back on the Raspberry Pi Software Configuration Tool, move the highlight to "Advanced" and press Enter to select.
- Select A4, Enable SSH server,
- Select Enable
- Back on the Raspberry Pi Software Configuration Tool, press the right arrow key to highlight "Finish," then press Enter twice to reboot.
- Upon rebooting, the Raspbian graphical desktop will appear.

 _(The preceding section was cut and pasted from the above site, it is NOT my work!)_

* * *

**Set up VNC so I can connect remotely and ditch the keyboard/mouse:**

[http://xmodulo.com/2013/12/remote-control-raspberry-pi.html](http://xmodulo.com/2013/12/remote-control-raspberry-pi.html)

_(The following is cut and pasted from the above site, it is NOT my work!)_

### VNC Service

Another way to access the entire Raspberry Pi desktop remotely is to install VNC server on Rasberry Pi. Then access the desktop remotely via VNC viewer. Follow instructions below to install VNC server on your Raspberry Pi.

$ sudo apt-get install tightvncserver

After the VNC server is installed, run this command to start the server.

$ vncserver :1

This command will start VNC server for display number 1, and will ask for a VNC password. Enter a password (of up to 8 characters). If you are asked to enter a "view-only" password, just answer it no ('n'). The VNC server will make a configuration file in the current user's home directory. After that, kill the VNC server process with this command.

$ vncserver -kill :1

Next, create a new init.d script for VNC (e.g., /etc/init.d/vncserver), which will auto-start the VNC server upon boot.

Now is a good time to see if you can SSH into the Pi, so you can paste this script in! :)

`$ sudo vi /etc/init.d/vncserver`

### BEGIN INFO
# Provides: vncserver
# Short-Description: Start VNC Server at boot time
# Description: Start VNC Server at boot time.
### END INIT INFO

#! /bin/sh
# /etc/init.d/vncserver
```
export USER='pi'
eval cd ~$USER
case "$1" in
start)
   su -c 'vncserver :1 -geometry 1024x768' $USER
   echo "Starting vnc server for $USER";;
stop)
   pkill xtightvnc
   echo "vnc server stopped";;
\*)
   echo "usage /etc/init.d/vncserver (start|stop)"
   exit 1 ;;
esac
exit 0
```

Modify the file permission so it can be executed.

`$ sudo chmod 755 /etc/init.d/vncserver`

Run the following command to install the init.d script with default run-level.

`$ sudo update-rc.d vncserver defaults`

Reboot your Raspberry Pi to verify that VNC server auto-starts successfully.

To connect via VNC Use `<IP Address>:1`, i.e.:

192.168.1.120:1

_(The preceding section was cut and pasted from the above site, it is NOT my work!)_

* * *

**Set up the WiFi card:**

Shut down the Pi and unplug it. (If you plug anything into the USB port while it is running you will cause it to reset because of the power surge.

`sudo shutdown -h now`

Now that you are in via VNC & SSH, unplug the keyboard and plug the WiFi Dongle in its place.

"WiFi Config" is right on the desktop. Run it and set up the WiFi, it is pretty easy.

Get the WiFi IP and test VNC and SSH on it.

Now this will not survive a reboot, so carry on to make it autostart:

[http://xmodulo.com/2013/12/remote-control-raspberry-pi.html](http://xmodulo.com/2013/12/remote-control-raspberry-pi.html)

`sudo vi /etc/network/interfaces`

Most of the required stuff was put in there by the GUI app, but not all,

Add:

`auto wlan0`

So that it looks like:

`pi@raspberrypi ~ $ cat /etc/network/interfaces`

```
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto wlan0
allow-hotplug wlan0
iface wlan0 inet manual
wpa-roam /etc/wpa\_supplicant/wpa\_supplicant.conf
iface default inet dhcp
```

Now reboot to see if it comes up on boot!

`sudo shutdown -r now`

Test VNC & SSH, and then unplug the keyboard and Ethernet and reboot again to see if we can work "cordless" (we still need power, but this is the idea anyway).

_NOTE: To reduce VNC traffic you may want to right click on the CPU monitor and remove it._

_You can do the same for the clock, now the screen should be static when nothing is happening, greatly reducing network traffic and WiFi dongle load on the power (battery?), not to mention the CPU load._

_You can also set your TightVNC session to 256 color from the client end to reduce traffic some._

_NOTE: If you disconnect abruptly, it does appear to keep your session open in the background._

* * *

**Set up SimpleIDE and program Propeller from Pi:**

[http://learn.parallax.com/propeller-c-set-simpleide/raspberrypi](http://learn.parallax.com/propeller-c-set-simpleide/raspberrypi)

_(The following is cut and pasted from the above site, it is NOT my work!)_

Install SimpleIDE?

- In the Raspbian desktop, open the Midori web browser and go to the Propeller Raspberry Pi page; [the top of this page](http://learn.parallax.com/propeller-c-set-simpleide/raspberrypi#RaspberryPiRelease).
- Download the SimpleIDE Raspberry Pi binary.
- Open the LXTerminal application. It should start up in your home directory right where Midori just saved the download. Type “ls” to verify.
- Use bunzip2 to unzip the archive by typing “bunzip2 -vv SimpleIDE\_0-9-45\_armv6l-RaspberryPi-Linux.tar.bz2” into the LXTerminal. (The actual file name may very). NOTE: For a shortcut to excessive typing, after entering the first unique letters of the file name “Simp,” press the tab key to auto-complete. Be patient, it will take more than five minutes to unzip.
- Then extract the files from the resulting tar file by typing “tar -xvf SimpleIDE\_0-9-45\_armv6l-RaspberryPi-Linux.tar” into the LXTerminal. Once again the tab key shortcut can be used to save on typing. This extraction process will take about two minutes.
- Move into the resulting SimpleIDE… folder by typing “cd SimpleIDE-0-9-45” into the LXTerminal. (The actual folder name may very).
- Run the setup script by typing “sudo ./setup.sh install” into the LXTerminal. This installation process will take about two minutes.

## Run SimpleIDE

- When installation is complete, run SimpleIDE by typing “simpleide” into the LXTerminal (from within the folder of the previous step).
- Verify and clear any first-time-run prompts. (Click "OK" on  any prompts about file location!)
- Connect your Propeller Activity Board to the external USB hub.
- Select the proper USB port in SimpleIDE’s port field.
- Now you can compile and download your code to the Propeller.

_(The preceding section was cut and pasted from the above site, it is NOT my work!)_

* * *

_NOTE: If you get "Cannot load empty board type" you probably have a dialogue box that popped up asking about file locations that you did not click "OK" on yet._

* * *

**Set to Text boot:**

As it is now, the Raspberry starts the XWindows GUI on the HDMI interface by default.

This uses a lot of memory, and if you are ONLY using it remotely it is a waste, so do this to make it boot to Text only:

`sudo raspi-config`

Select "3 Enable Boot to Desktop/Scratch"

Select "Console Text console"

Use right arrow to select "<Finish>"

Reboot: Yes

Now it should boot with a text only prompt, but you can still use VNC to get a GUI!

This seems to make everything a LOT peppier!

Remember you can grab files from your desktop with FTP/SFTP. ;)

* * *

**Install SFTP Client on Pi:**

`sudo apt-get install filezilla`

When it is done there should be a Filezilla icon under Internet in the menu.

* * *

**Shutdown:**

`sudo halt -h`

or

`sudo shutdown -h now`

Then wait, the WiFi dongle blue light will go off, and all lights except for power will eventually quit.

The ACT (green) LED will blink ten times when the Pi is full shut down. Then you can safely unplug it!
