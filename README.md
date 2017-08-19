# AntergosPrime

### This collection of scripts wants to provide GPU-switching for Hybrid-GPUs like in \*buntu-distributions for Antergos.

This branch is a fork of emanuellopes's [archLinuxPrime](https://github.com/emanuellopes/archLinuxPrime) which got optimized for the Antergos distribution. Emanuellopes forked for his repo the prime application that comes on Linux Mint.

Even if this branch is made for Antergos, the installation-instructions are mostly system-independent and should therefore work with any Arch-distribution.

### Status
Currently this script only works with the display manager SDDM and **NOT** with Antergos's default display manager LightDM.
However switching is easy, so it should be not a big deal to switch your display manager.
The prime-indicator does also not work - currently function goes before accessibility ;) 

### Why not solution XYZ?

You might ask why to use this config and not something like Bumblebee. It's simple: if your laptop has the HDMI-output hardwired to your Nvidia GPU and you can not disable any GPU inside your BIOS/UEFI, then you won't be able to switch GPUs. 

If you can not switch GPUs you have to let your Nvidia-GPU activated the whole time, so that you can use the HDMI-output and do graphical stuff like Gaming. In terms of battery run-time you will see that you can not really use your laptop to go this way since the battery will drain very fast.

With AntergosPrime you can switch GPUs easily, similar to \*buntu-distributions. It's of course not perfect, e.g. you have to logout for GPU switching, but at least you can use both GPUs. Other solutions for this type of setup have serveral drawbacks, as mentioned below.




**Bumblebee**

With Bumblebee you can only use the tool "intel-virtual-output", if your HDMI-output is hardwired to the Nvidia-GPU, however it works rather bad and has bad performance (especially if you want to game on a second screen). More Information to intel-virtual-output and Bumblebee can be found [here](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup).  

**nvidia-xrun**

There are solutions like nvidia-xrun, the problem with nvidia-xrun is that you have to switch to an unused TTY and also Steam does not work. You can found more information about nvidia-xrun [here](https://github.com/Witko/nvidia-xrun).



## Installation

**Install bbswitch and SDDM (if not installed)**
```
sudo pacman -S bbswitch sddm
```

**Download all needed files manually or with the command "git clone"**
```
git clone https://github.com/konstantingoretzki/AntergosPrime
```

**Switch to the folder "AntergosPrime" and run the install.sh**
```
./install.sh
```
If you can not run the install.sh then check out, that you have execute-permissions.
```
chmod +x install.sh
```

**Note:**
The process is the same if you want to remove AntergosPrime. This time just run remove.sh.
