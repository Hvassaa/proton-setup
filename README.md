# How to set up "steam play"/proton *on my setup*

Last updated on 16. September, 2018
My specific  setup is ubuntu 18.04 with a r9 280x GPU

## Based on
* https://github.com/ValveSoftware/Proton
* https://github.com/ValveSoftware/Proton/blob/proton_3.7/PREREQS.md
* https://askubuntu.com/questions/927601/i-think-im-using-radeon-instead-of-amdgpu-how-do-i-change
* https://wiki.archlinux.org/index.php/AMDGPU

## What to do? 
* Install steam, obviously. (Through the repos!)
* Opt into steam beta by
    * Going into settings (in the menu at the top)
    * Choose the account tab
    * Under "Beta participation" click "CHANGE..."
    * Change it from "NONE" to "Steam Beta Update"
    * Restart steam
    * Go into Settings again
    * *optional* Under the "Steam Play" click "Enable Steam Play for all titles" and then restart steam
* Make sure you have python3 and python2.7 installed
* Make sure AMDGPU is installed
* Possibly install alot of different vulkan and other graphic packages? - may already be okay (some will be installed in later steps as well)
* Add some ppa for newer (and required) mesa and LLVM and install them
    * sudo add-apt-repository ppa:paulo-miguel-dias/mesa
    * sudo apt update
    * sudo apt dist-upgrade
    * sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
    * Install LLVM? 
* Now you should make sure you're using AMDGPU and not just radeonv
    * Edit /etc/default/grub by adding "radeon.si_support=0 amdgpu.si_support=1" to the GRUB_CMDLINE_LINUX_DEFAULT="PUT IT HERE"
    * *for southern islands (SI) it should be* 
        * GRUB_CMDLINE_LINUX_DEFAULT="radeon.si_support=0 amdgpu.si_support=1"
    * Before the edit, the line would have been GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and you can let "quiet splash" stay if you want
    * run sudo update-grub
* Reboot and you're done
