---
{"title":"Use a Raspberry Pi and Asterisk to turn an old Alarm System into a Home Monitor","created":"2015-04-02","categories":["home-automation"],"authors":["hoopy"],"dg-publish":true,"permalink":"/ancient-history/2015/use-a-raspberry-pi-and-asterisk-to-turn-an-old-alarm-system-into-a-home-monitor/","dgPassFrontmatter":true}
---

*Posted: April 2, 2015*

If you have an old alarm system that is capable of calling a remote monitoring station, and you want to just turn it into a fancy "chime" instead that can notify your phone. Please note that this is not reliable enough to be considered a "security" system. But if you don't even use your alarm system anymore, or quit paying for the monitoring service, this will add some fun features!

The orginal source for the Raspberry Pi intall of Asterisk is here: [http://nerdvittles.com/?p=3026](http://nerdvittles.com/?p=3026 "Nerd Vittles Asterisk for Pi")

Here is how I connected it all to my old alarm system.

First, you need an alarm system. I have an old [GE Interlogix Simon 3 Wireless Security System](http://www.homesecuritystore.com/ge-interlogix-80-307-3x "GE Interlogix Simon 3"), so these instructions work for this model.

![Simon](/img/user/attachments/Simon.jpg)

In theory this will work with any alarm system that can dial out to a monitoring station via plain old telephone lines. The secret sauce is in a file called app\_alarmreceiver.c You may have to replace and/or edit and recompile this file to get it to work with your particular system. I will cover that later.

Second, you need either a dedicated Linux computer to run Asterisk, or a Virtual Machine running Asterisk 24x7, or a Raspberry Pi B or better! You do not need the latest model, just make sure it has 512 MB of memory and it will work.

Third, you need an "ATA". An ATA is a box with phone jacks and an Ethernet connection. It allows you to plug a normal phone into it and receive dial tone, accept touch tones and send them over TCP/IP to anywhere in the world. I am using the [Grandstream GS-HT702 Handytone 2-FXS Port Analog Telephone Adapter](http://www.amazon.com/gp/product/B007PEIHKE/ref=oh_aui_search_detailpage?ie=UTF8&psc=1 "ATA") from Amazon, so if you want one that is tested for this, use that. You do not need two phone jacks though, so you could use a cheaper single jack model. I got the two jack model so that I could experiment with other uses on the second line.

Note that I will not be covering any setup of external VoIP providers or anything here, but in theory you can do all kinds of things with this box once it is done.

**Install PBX In A Flash:** Download incrediblepi-**3.6**.tar.gz from [http://sourceforge.net/projects/pbxinaflash/files/IncrediblePi-1.x-Debian-6/](http://sourceforge.net/projects/pbxinaflash/files/IncrediblePi-1.x-Debian-6/) **NOTE: Watch the versions! I am still on version 3.6!** Version 3.7 \*MIGHT\* work, but I am sure nothing newer will! The 3.11.x versions use Asterisk 11 and those did not work for me. Only try them if you are interested in experimenting, otherwise stick with **3.6**.

Extract the files (I used the 7zip 64 bit install on my Windows box) Use win32 Disk Imager to write the image to the SD card Put the SD into my Raspberry Pi, plug in TV, and Ethernet and power and watch it boot up! The Pi should read its IP address out loud if you have speakers or headphones plugged into it!

NOTE: When I say "ssh" you can use [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html "PuTTY") if you are on Windows.

ssh root@ip-address-of-your-pi

Password: raspberry

Hit Enter to let it start downloading updates.

Set new root password!

Set Timezone (America, Chicago) or whatever yours is.

Run: /root/update-my-pi (should show nothing to update, since it just did this on login)

Run: raspi-config

This will give you lots of fun options, use this anytime, but now is best for some things.

Select: "expand\_rootfs" Then go to "Finish" when it is done, and tell it "Yes" to reboot.

ssh root@ip-address-of-your-pi ctrl-cl to skip updates

\# For some reason the install doesn't include vi! apt-get update # This only updates the local package index, it doesn't change anything, so "update" is safe. # Without it you get errors about not finding stuff because it has been moved around apt-get install vim

vi /etc/profile.d/helloworld.sh #/root/update-my-pi # So it doesn't ask you to update on every login! echo "/usr/local/sbin/status" # So it doesn't run this and clog up logins

**IP & Hostname:** IF you want to set up a static IP on the Raspberry PI do this. Your ATA will need to talk to the Pi, so it is good if the IP does not change, although it can use a hostname. Also, using Google's DNS servers works well for me. Source: [http://pbxinaflash.com/community/index.php?threads/static-ip-for-raspberry-pi.14364/](http://pbxinaflash.com/community/index.php?threads/static-ip-for-raspberry-pi.14364/)

I'm using 192.168.1.1 here, but use an address that works on your network!

vi /etc/network/interfaces iface eth0 inet dhcp iface eth0 inet static address 192.168.1.1 netmask 255.255.255.0 gateway 192.168.1.254 dns-nameservers 8.8.8.8 8.8.4.4 Set IP to 192.168.7.2 in Router's Static config.

To change the hostname to "Pi" run: hostname Pi

vi /etc/hosts # replace all instances of incrediblepbx with Pi vi /etc/hostname # Replace incrediblepbx with Pi shutdown -r now

**Open up iptables for SSH from outside:** add this line to /etc/network/iptables and reboot: iptables -A INPUT -p tcp -m multiport --dports 22 -j ACCEPT Run this to list active entries: iptables --list

Put http://192.168.1.1/ (or whatever IP you chose) in your web browser and click on FreePBX Administration

Username: admin Password: admin

1\. Changing FreePBX admin Password and Default Email. From the main FreePBX GUI, click Admin => Administrators. Click on admin user in the far-right column. Enter a new Password and click Submit Changes button. Then click the Apply Config button. Next, set your default email address at the bottom of Settings -> General Settings. Repeat the procedure above to save your entry.

Set up 701 for use with ATA Applications->Extensions->701 secret: 13n38j (You may want to set your own, just keep it consistent!) dtmfmode: In band audio allow: ulaw permit: 192.168.1.0/255.255.255.0 submit apply config

**Set up your ATA:** The HT702 manual is here: [http://www.grandstream.com/products/ht\_series/ht701/documents/ht70x\_usermanual\_english.pdf](attachments/ht70x_usermanual_english.pdf)

Hook it up to the network, power and plug in a phone. pick up the handset and dial \*\*\* then dial 02 It should announce its IP address.

Enter it into a web browser. The default password is "admin" for admin use.

First thing is to get the latest firmware!

Download latest firmware from [http://www.grandstream.com/support/firmware](http://www.grandstream.com/support/firmware)

NOTE: I am on firmware version 1.0.4.11 I have found that sometimesa version does not work, so once you get it working, don't upgrade it again unless you have time to debug!

Upload firmware through Advanced Settings:

INSTRUCTIONS FOR UPLOAD FROM LOCAL DIRECTORY: 1- Download the firmware file from Grandstream web site 2- Unzip it and copy the file in to a folder in your PC 3- From the HT70X web interface (Advanced Settings page) you can browse your hard drive and select the folder you previously saved the file (ht70xfw.bin) 4- Click “Upload Firmware” and wait few minutes until the new program is loaded.

Note: Always check the status page to see that the program version has changed.

To reset to defaults: Basic Settings->Reset Type: Full Reset->Reset

Basic Settings: Set a new End User Password and record it. Time Zone: GMT -06:00 (Central Time) or whatever yours is. (If this doesn't account for Daylight Savings, then define a custom one) "Update"

Advanced Settings: Set an Admin Password and record it. #Firmware Server Path: firmware.grandstream.com CHECK - Always Skip the Firmware Check Syslog Server: 192.168.1.1 (Your Pi's IP address) Syslog Level: INFO "Update"

FXS PORT1 Primary SIP Server: 192.168.1.1 (Your Pi IP Address) SIP User ID: 701 Authenticate ID: 701 Authenticate Password: 13n38j Name: 701 "Update"

FXS PORT2 Primary SIP Server: 192.168.1.1 (Your Pi IP Address) SIP User ID: 702 Authenticate ID: 702 Authenticate Password: 13n38j Name: 702 Preferred DTMF method: Set all 3 to "In-audio" Offhook Auto-Dial: 85764 (This makes it VERY fast, because it dials immediately, just set the alarm to dial a #, which is normally redial, but the ATA forgets the last number dialed every time you reset it, also, this means that if you don't know how to change the number that your alarm system dials out, it doesn't matter, the ATA will dial for it and ignore whatever phone number the alarm system tries to dial!) "Apply" Reboot

**Direct incoming calls to extension 701:** Connectivity -> Inbound Routes -> Default. In the Set Destination section of the form, change the target to Extensions and then select 701 from the list. Then clickSubmit and Apply Config.

Set up Extension 702 on Asterisk for Alarm System: [http://www.freepbx.org/forum/freepbx/users/alarmreceiver-howto-get-it-to-work](http://www.freepbx.org/forum/freepbx/users/alarmreceiver-howto-get-it-to-work)

Edit /etc/asterisk/extensions\_custom.conf and add this at the bottom ; Alarmreceiver \[custom-myalarmreceiver\] exten => s,1,NoOp(Alarm received) exten => s,n,System(/etc/asterisk/PreAlarmNote) exten => s,n,Answer exten => s,n,AlarmReceiver exten => s,n,Hangup

NOTE: /etc/asterisk/PreAlarmNote is a script I wrote that sends me a PushOver notice and plays a sound from the Pi whenever an alarm notice comes in.

In FreePBX go to Admin, Custom Destinations

Enter in Custom Destination this custom-myalarmreceiver,s,1 In Description enter Alarm Receiver Submit Changes Apply Config

**Set up Alarm Receiver:** Download: alarmreceiver.conf AlarmCommand PreAlarmNote from [my GitHub Repository](https://github.com/chrisl8/app_alarmreceiver.c), and put them in /etc/asterisk cd /etc/asterisk chmod +x AlarmCommand chmod +x PreAlarmNote mkdir /eventArchive/ chmod a+w /eventArchive/

PreAlarmNote and AlarmCommand are stripped down copies of my scripts. You need to open them and edit them to match your system and do things for you. As they are now, they will not do anything.

In Web admin interface: Applications->Extensions->Add Extension Generic SIP, Submit User Extension: 702 Display Name: 702 secret: 13n38j dtmfmode: In band audio nat: Yes Submit Click on 702 again allow: ulaw permit: 192.168.1.0/255.255.255.0 submit apply config

Applications->Misc Applications Add Description: Alarm Call Center Feature Code: 85764 Destination: Custom Destinations:Alarm Receiver "Submit Changes" "Apply Config"

**Recompile Asterisk with with new alarmreceiver:** This is the important part that made my system work. It is possible that YOUR system does not need this step, or that you will have to make more or different changes to app\_alarmreceiver.c for your particular system.

Reference: [http://www.pbxinaflash.com/community/index.php?threads/dropped-calls-after-15-minutes.7604/#post-82159](http://www.pbxinaflash.com/community/index.php?threads/dropped-calls-after-15-minutes.7604/#post-82159)

amportal stop cd /usr/src wget http://downloads.asterisk.org/pub/telephony/asterisk/releases/asterisk-1.8.17.0.tar.gz tar zxvf asterisk-1.8.17.0.tar.gz rm asterisk-1.8.17.0.tar.gz mv asterisk-1.8.17.0 asterisk

cd asterisk/apps/ mv app\_alarmreceiver.c /root/ORIGapp\_alarmreceiver.c

Download: app\_alarmreceiver.c from [my GitHub Repository](https://github.com/chrisl8/app_alarmreceiver.c), and put it here in /usr/src/asterisk/apps/

cd .. make clean ./configure # Make your putty window full screen, or you will get an error about minimum terminal size make menuselect # Select "res\_config\_mysql", "app\_mysql" and "cdr\_mysql" from the top item "Add-ons" make make install

NOTE: This output was seen, but it did not appear to cause any problems: Your Asterisk modules directory, located at /usr/lib/asterisk/modules contains modules that were not installed by this version of Asterisk. Please ensure that these modules are compatible with this version before attempting to run Asterisk. app\_flite.so cdr\_sqlite.so chan\_mgcp.so res\_config\_sqlite.so WARNING WARNING WARNING

amportal start

You can go to the Linux prompt and run asterisk -vvvvvvvvvvr to get a an Asterisk command line and watch the log

**That is it! Plug in your alarm system's phone line to the ATA port 2, arm it, and see if it starts talking to your Asterisk install and making things happen!** Note that most systems only dials out when they are ARMED, so you have to leave it armed for this to work. The two options are to disable all sirens and use it as a sort of "chime" system, or only get notices when the system is armed. Either way, you have to arm it to test it now.

**FreePBX Module Updates** FreePBX will tell you about modules that need to be updated, and you should do these. Be ware of anything that says it will update Asterisk though, and don't install anything new unless you know what you are doing. But the updates for the installed modules should be installed for security issues.

**Below are some issues that came about as I updated things:**

**Ensure FreePBX Admin page works:** Reference: http://www.freepbx.org/forum/beta-program-issues/menus-are-not-displaying-correctly-image-attached Sometimes the menu at the top of the FrePBX Admin pages looses all of its buttons and turns into small text with small text drop downs that are very hard to use, not to mention a lot of other bits of the page are malformed. Do this to prevent that: http://192.168.1.1/ (or whatever your IP is) FreePBX Administration Settings->Advanced Settings Disable Mainstyle CSS Compression: True Apply

That should fix/prevent that problem.

**udptl\_custom.conf** Reference: [http://www.freepbx.org/forum/general-help/help-please-symlink-from-modules-failed](http://www.freepbx.org/forum/general-help/help-please-symlink-from-modules-failed) I started getting this error in FreePBX after some updates:

retrieve\_conf failed to sym link: /etc/asterisk/udptl.conf from core/etc (Already exists, not a link) This can result in FATAL failures to your PBX. If the target file exists and not identical, the symlink will not occur and you should rename the target file to allow the automatic sym link to occur and remove this error, unless this is an intentional customization. Added 4 minutes ago (retrieve\_conf.SYMLINK)

The solution appears to be:

mv /etc/asterisk/udptl.conf /etc/asterisk/udptl\_custom.conf

Then do an "apply changes" in the FreePBX admin (you may have to fiddle with something to get the "apply changes" to appear.

Note that the /etc/asterisk/udptl.conf should now be a link to /var/www/html/admin/modules/core/etc/udptl.conf and that includes udptl\_custom.conf

**Default ARI Admin password Used** Somewhere in the FreePBX updates we got an "ARI Password" in amportal.conf I \*think\* that this is used for the "Voicemail & Recordings (ARI)" page.

root@Pi:~# grep ARI /etc/amportal.conf ARI\_ADMIN\_USERNAME= ARI\_ADMIN\_PASSWORD=ari\_password

But DO NOT change it here, instead go to Settings->Advanced Settings and set it!

Default Asterisk Manager Password Used You are using the default Asterisk Manager password that is widely known, you should set a secure password Added 94 weeks, 5 days, 23 hours, 48 minutes ago (core.AMPMGRPASS)

This you should be able to set in Settings->Advanced Settings I set it to the same ad the FreePBX password from LastPass (admin/)
