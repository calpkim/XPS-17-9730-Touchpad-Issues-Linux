# XPS-17-9730-Touchpad-Issues-Linux
## For Dell XPS 17 9730 (2023) Debian
Inspiration from Omo, https://gist.github.com/omo/4839c896019980d4f9d49aeff3c25929
## THIS IS FOR WAYLAND, if you are running X, I have not confirmed whether this works on X. For a better outcome, I recommend checking out Omo's comments
## 1: Checking the Kernel
The error is most likely caused by a `PS/2 Generic Mouse` kernel. To check, run `lsmod | grep psmouse`. If the output gives anything, that is your problem. 
## 2: Blacklisting Kernel
To fix the issue, we must prevent it from starting on boot. To do so, we must Blacklist it.
Create (or edit) a file, `sudo nano /etc/modprobe.d/blacklist.conf` and paste `blacklist psmouse`. Save, exit, update the boot config to read the Blacklist file `sudo update-initramfs -u`, and reboot (`sudo reboot`)
## 3: Ensuring problem is fixed
Upon reboot, run `lsmod | grep psmouse` and make sure the command outputs nothing. If so, the touchpad should work all good now.
If the problems persist, I am very sorry, as of yet, I am unaware as to how to help you. If the kernel is still active, go through the steps again and make sure you pasted correctly and you then updated the initramfs. 
