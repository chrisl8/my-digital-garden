---
{"dg-publish":true,"permalink":"/knowledge-base/disable-vt-d-on-thinkpad-to-enable-wsl-2/"}
---

*Posted: February 14, 2023*
# BSOD on Reboot with WSL2
Windows 11 Update 22H2 with BSOD on boot if you either install WSL2 or update to 22H2 after WSL2 is installed.

On my Thinkpad and apparently many Dell XPS machines post Windows 11 update 22H2 you must disable VT-d or else Windows will BSOD when attempting to reboot after installing WSL2.
Or if you install WSL2 before updating to 22H2 it will BSOD.

This is known as "Virtualization Direct I/O" in most places

 - Open the BIOS and find the CPU Virtualization section and set it up like so
![attachments/Pasted image 20230219230456.png](/img/user/attachments/Pasted%20image%2020230219230456.png)
Note that Kernal DMA Protection must apparnetly be disabled in order to disable VT-d, but of course leave "Virtualization" in general enabled lest WSL cannot work at all.

There are a few posts about this issue online:
 - https://github.com/microsoft/WSL/issues/4784
 - https://forums.lenovo.com/t5/ThinkPad-P-and-W-Series-Mobile-Workstations/Thinkpad-P73-Windows-11-22H2-won-t-boot-with-VT-D-HyperV-WSL2-enabled/m-p/5195808
 - https://answers.microsoft.com/en-us/windows/forum/all/windows-11-22h2-getting-stuck/de6fdc6d-2fb9-4e76-b3df-c14cf6c1774e?page=1
 - https://www.reddit.com/r/WindowsHelp/comments/xkftil/comment/irjq6ww/

As far as I can tell Virtualization Direct I/O may be as much a security benefit as it is a speed enhancement, if it enhances speed at all.
It is also focused more on handing over control of entire devices to the VM, not sharing, so it might be more important when giving a NIC or GPU to a VM in a server situation. At least maybe.
Anyway, it crashes my laptop, so shut it off!

#Windows #KnowledgeBase 