# NVIDIA Install

https://communities.vmware.com/t5/Photon-OS-Discussions/NVidia-Triton-on-Photon-OS/m-p/2926221
https://plmlab.math.cnrs.fr/plmshift/gpu_driver/-/blob/master/photon3.0/Dockerfile


```
# required
tdnf install tar

nvidia_binary_version="470.57.02"
nvidia_binary="NVIDIA-Linux-x86_64-${nvidia_binary_version}.run"
wget -q https://us.download.nvidia.com/XFree86/Linux-x86_64/${nvidia_binary_version}/${nvidia_binary} 
chmod +x ${nvidia_binary}
./${nvidia_binary} --accept-license --ui=none --no-kernel-module --no-questions
```

Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 470.57.02...

Welcome to the NVIDIA Software Installer for Unix/Linux

Detected 32 CPUs online; setting concurrency level to 32.
Not installing a kernel module; skipping the "is an NVIDIA kernel module loaded?" test.
Installing NVIDIA driver version 470.57.02.

WARNING: You specified the '--no-kernel-module' command line option, nvidia-installer will not install a kernel module as part of
         this driver installation, and it will not remove existing NVIDIA kernel modules not part of an earlier NVIDIA driver
         installation.  Please ensure that an NVIDIA kernel module matching this driver version is installed separately.


WARNING: nvidia-installer was forced to guess the X library path '/usr/lib64' and X module path '/usr/lib64/xorg/modules'; these
         paths were not queryable from the system.  If X fails to find the NVIDIA X driver module, please install the `pkg-config`
         utility and the X.Org SDK/development package for your distribution and reinstall the driver.


WARNING: Unable to find a suitable destination to install 32-bit compatibility libraries. Your system may not be set up for 32-bit
         compatibility. 32-bit compatibility files will not be installed; if you wish to install them, re-run the installation and
         set a valid directory with the --compat32-libdir option.

Searching for conflicting files:
  Searching: [##############################] 100%
Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (470.57.02):
  Installing: [##############################] 100%
Driver file installation is complete.
Running post-install sanity check:
  Checking: [##############################] 100%
Post-install sanity check passed.
Running runtime sanity check:
  Checking: [##############################] 100%
Runtime sanity check passed.
Would you like to run the nvidia-xconfig utility to automatically update your X configuration file so that the NVIDIA X driver
will be used when you restart X?  Any pre-existing X configuration file will be backed up. (Answer: No)

Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 470.57.02) is now complete.  Please update your
xorg.conf file as appropriate; see the file /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.
