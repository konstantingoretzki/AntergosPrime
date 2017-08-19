# AntergosPrime

### This collection of scripts wants to provide GPU-switching for Hybrid-GPUs like in \*buntu-distributions for Antergos.

This branch is a fork of emanuellopes's [archLinuxPrime](https://github.com/emanuellopes/archLinuxPrime) which got optimized for the Antergos distribution. Emanuellopes forked for his repo the prime application that comes on Linux Mint.

Even if this branch is made for Antergos, the installation-instructions are mostly system-independent and should therefore work with any Arch-distribution.

### Status
Currently this script only works with the display manager SDDM and NOT with LightDM.
The prime-indicator does also not work.

## Installation

Install bbswitch and SDDM (if not installed)
```
sudo pacman -S bbswitch
```

