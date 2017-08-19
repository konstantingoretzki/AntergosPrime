# AntergosPrime

### This collection of scripts wants to provide GPU-switching for Hybrid-GPUs like in \*buntu-distributions for Antergos.

This branch is a fork of emanuellopes's [archLinuxPrime](https://github.com/emanuellopes/archLinuxPrime) which got optimized for the Antergos distribution. Emanuellopes forked for his repo the prime application that comes on Linux Mint. 

The main work of this script goes to Emanuellopes and the Linux-Mint-team, I just optimized on some paths, updated package names, added how to fix the tearing and put everything well described together, so that even people with less bash skills can (hopefully) easily follow on how to install and use AntergosPrime.

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

## DO NOT INSTALL - The AntergosPrime repo is not ready for usage

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
cd AntergosPrime
```
```
./install.sh
```
If you can not run the install.sh then check out, that you have execute-permissions.
```
chmod +x install.sh
```

**Note:**
The process is the same if you want to remove AntergosPrime. This time just run **remove.sh**.


If everything worked we have now to disable or delete the old display manager (LightDM) and activate our new installed display manager SDDM. Be careful while doing, if your forget to enable SDDM you won't be able to use your desktop environment.

**Disable LightDM**
```
sudo systemctl disable lightdm
```

**Enable SDDM**
```
sudo systemctl enable sddm
```

## Usage 

Now you can switch GPU-configs with "prime-select". It's a good idea to try both configs, so that everything is installed.

**Intel**
```
sudo prime-select intel
```

**Nvidia**
```
sudo prime-select nvidia
```

**Note:** If there's an update e.g. for Nvidia or nvidia-utils, you have to switch to both GPUs once with **prime-select** so that all the Xorg-files are in place and overwrite the new generated files by the update.

## Tearing while using the Nvidia-GPU
Even if Emanuellopes tried to fix the tearing while using the Nvidia-GPU, it still does not work and gives your terrible tearing.

The solution I found was to use [PRIME Synchronization](https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/).

The setup with AntergosPrime is rather simple, since the script do provide almost everything needed (all needed modules are loaded).

The only thing that has to be done manually is to add the kernel-parameter ```nvidia-drm.modeset=1``` to GRUB (if you don't use GRUB, look your needed setup up in the [ArchWiki](https://wiki.archlinux.org/index.php/Kernel_parameters).

### GRUB

**Edit /etc/default/grub**
```
sudo nano /ect/default/grub
```

**Append the kernel options to the GRUB_CMDLINE_LINUX_DEFAULT line**
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nvidia-drm.modeset=1"
```

**Re-generate the grub.cfg file**
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

You should now be able to switch on and off PRIME Synchronization.
You can do this with ```xrandr --output [your-screen-name] --set "PRIME Synchronization" 1```

Disabeling is the same, just use "0" instead of "1".
If you're using KDE, you can easily get your screen-name by KDE's display setup menu.

Inside the folder "tearing" of this repo are the two files **kill_vsync.sh** and **start_vsync.sh**, with these files you can easily turn PRIME Synchronization on and off - just execute them.


## Troubleshooting

### After an update it does not work anymore!
**Solution:**
Try to switch to both GPUs with **prime-select** once, so that all the Xorg-files are in place and overwrite the new generated files by the update.

### All fonts are very small!
**Solution:**
Add ```xrandr --dpi [wished DPI]``` to your files **nvidia-optimus.sh** and **Xsetup**.
If you want to use my dpi-settings, then just uncomment the line ```xrandr --dpi 96``` in both files.

### I get the error ```bash: ./install.sh: Permission denied```!
**Solution:**
Just make the file executable with ```chmod +x install.sh```.
