# Fixing AMD 780M/7XXM iGPU freezes on Linux

As of the time I'm writing this, the Linux driver for AMD GPUs has a bug which affects the 780M iGPU and other iGPUs of the same series. At seemingly random moments and intervals, your whole graphics can crash, resulting in a complete freeze of your display which lasts forever, requiring a force shutdown of your system. Your system and the rest of the hardware is still working, but the graphics remain unresponsive.

This is a bug currently being worked on in the AMD drivers, see here: https://gitlab.freedesktop.org/drm/amd/-/issues/4141


If you suffer from this issue and have an affected iGPU, there are 2 workarounds you can do to circumvent the problem:

## Workaround 1

Add the following option `amdgpu.dcdebugmask=0x10` or `amdgpu.dcdebugmask=0x12` to the kernel parameters. This fixes the freezes but can increase GPU power consumption as a drawback.

## Workaround 2

Add the following option `amdgpu.gpu_recovery=1` to the kernel parameters. This option does not fix the display freeze issue, but once it happens, the GPU will timeout and the graphics will restart. This is an alternative to the first workaround which shouldn't increase power consumption.


## How to set kernel parameters (Grub)

This guide assumes you are using Grub as your bootloader. For other ways to configure kernel parameters, see [here](https://wiki.archlinux.org/title/Kernel_parameters).

* As root, open the file located in `/etc/default/grub` with a text editor
* Find the line which starts with `GRUB_CMDLINE_LINUX_DEFAULT` and add the parameters shown in the workarounds here. Parameters are separated by spaces and the whole command-line must be included inside the quotation marks.
* Save the file
* As root, run `update-grub`
* Restart system

Example: `GRUB_CMDLINE_LINUX_DEFAULT="modules=sd-mod,usb-storage,ext4,nvme,vmd quiet rootfstype=ext4 amdgpu.gpu_recovery=1 amdgpu.dcdebugmask=0x10"`
