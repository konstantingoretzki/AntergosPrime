# AntergosPrime

### This collection of scripts wants to provide GPU-switching for Hybrid-GPUs like in \*buntu-distributions for Antergos.

This branch is a fork of emanuellopes's [archLinuxPrime](https://github.com/emanuellopes/archLinuxPrime) which got optimized for the Antergos distribution. Emanuellopes forked for his repo the prime application that comes on Linux Mint.

Even if this branch is made for Antergos, the installation-instructions are mostly system-independent and should therefore work with any Arch-distribution.

### Status
Currently this script only works with the display manager SDDM and NOT with LightDM.
The prime-indicator does also not work.

### Why not solution XYZ?

You might ask why to use this config and not something like Bumblebee. It's simple: if your laptop has the HDMI-output hardwired to your Nvidia GPU and you can not disable any GPU inside your BIOS/UEFI, then you won't be able to switch GPUs. 

**Bumblebee**
With Bumblebee you can only use the tool "intel-virtual-output", if your HDMI-output is hardwired to the Nvidia-GPU, however it works rather bad and has bad performance (especially if you want to game on a second screen). More Information to intel-virtual-output and Bumblebee can be found [here](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup).  

**nvidia-xrun**
There are solutions like nvidia-xrun

## Installation

**Install bbswitch and SDDM (if not installed)**
```
sudo pacman -S bbswitch sddm
```

