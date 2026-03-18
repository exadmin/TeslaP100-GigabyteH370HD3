# How to setup Tesla P100 video-card in compute mode on Gigabyte H370 HD3 (rev.1) motherboard
### My initial configuration
Motherboard = Gigabyte H370 HD3
CPU = Intel Core i5-8400
Mem = 64Gb (DDR4 16Gb x 4, 2400 MT/s)
BIOS = "F10" version

### Required setting in BIOS
0. Update BIOS version up to F17 (tested with this on, cause "Bar Resize" option is not availabel at F10 version for example). Not - my pre-installed Windows 11 was not able to start normaly after BIOS update. I didn't research the issue and didn't try to troubleshoot it - cause it was easier for me to run Windows clean installation in background on my workstation.
1. Intel Platform Trusted Technology = Enabled (Required for Windows 11 installation)
2. Above 4G Decoding = Enabled (Required for Video Card to use 16Gb of VRAM)
3. CSM Support = Disabled (Required for full UEFI mode)
4. Bar Resize = Auto (Required for Video Card to use 16Gb of VRAM)

### Install Windows 11
I've tested all with Windows 11 Pro installed in UEFI mode

### Install Nvidia drivers
You need to install Nvidia Data Center Drivers, you can find required version at official site: https://www.nvidia.com/en-us/drivers/
I've used Tesla P100 version for Windows 11 with CUDA 12.2 (cause latest one v13.1 in v.591.59 were unbale to be installed during my previous tries).
Run installation in Custom Mode - deselect "RTX Control Panel" - just install Drivers.

After installation check Windows "Device Manager" - the Tesla P100 video-card should operate normally.
If you see error "Code 12", message like "Video card can't use all availabel resources" - please check BIOS seettings mentioned above.

### Ollama
Modern version of Ollama does not require any setup, I've found Tesla P100 usage by default.
You can find Tesla usage in "Nvidia GPU Utilization" of Nvidia Control Panel 

Useful links I've found:
* Gigabyte Drivers: https://www.gigabyte.com/Motherboard/H370-HD3-rev-10/support
* Nvidia Drivers: https://www.nvidia.com/en-us/drivers/
* Switching Tesla P100 into WDDM: https://github.com/FilipchukAl/launch_Tesla_P100 (didn't tested yet)