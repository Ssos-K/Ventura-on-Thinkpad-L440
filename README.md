# Ventura-on-Thinkpad-L440 Haswell
This is a Ventura Hackintoshing on Haswell with Graphics Acceleration of 4th Generation Laptop.
For this to boot well, i threw in all the boot-args; keepsyms=1 amfi_get_out_of_my_way=0x1 ipc_control_port_options=0 -no_compat_check
First the Specs of Laptop are Lenovo ThinkPad L440 core i7 Quard with 2.5GHz Speed, 16GB Ram, 256 SSD, and Intel HD4600 Graphics. 
Please note that this EFI was tested with Ventura 13.0, and on 13.6 it had issues so it seems the more updated Ventura OS doesnt work well.
In the Bios, make sure that you boot with UEFI with CSM, when you disable CSM, you get gabbled screen at login. To make this a success, ensure 
that you PC runs Monterey well, then change your SMBios and use MacBookPro15,3. use GenSMBios to get correct values. If you use this EFI without
changing that Serial indicated, you will not be able to sign-in iCloud, so first you must change Serial number to use iCloud.
If you want to use this EFI directly and you have same machine, then install with Ventura 13.0, which is what i tested with and its what i use, 
i disabled updates as they may break System.
Here are the steps; 
Grab a copy of Ventura 13.0, and make bootable USB. In my case i attached SSD to another Mac, partitioned it into a 20GB partition (Extended JHFS+) where 
i put the installer, and the remaining partition was left for the installation. Then used this EFI and placed it on SSD EFI partition and kept a copy of
OCLP 0.62. So you can put EFI on your USB and boot from that. 
Start PC and boot from created USB (In my case SSD booted from EFI into installation)
At Welcome, go to Diskutility and format partition or drive with APFS, the close Diskutility and continue with installation. If you leave EFI on flash, 
then at every boot you chose USB. In my case i just took a nap since EFI was on SSD and at every reboot, things were going by themselves. Only later to 
see welcome and Setup user up to desktop. The Graphics is sluggish at this stage, so because this EFI disables Securebootmode and AMFI, Open up OpenCore
Legacypatcher 0.62 and click root patching, you will see Interl Haswell already identified and proceed with root patching.
This is important!!!
In order for Root patching to successfully add IntelHD Haswell drivers, as Patching begins or before it starts, open System Prefarances and go to 
Privacy and Security and keep watching that area. If you don't do that you may never see the notification of system extensions that need permission and
once you don't get that, graphics drivers will not be allowed to run.
After Installation of drivers by OCLP, the system will ask you to open Privacy and Security to allow extensions. If it is already open, some notification 
will show up and click allow, after it will ask you for password and to reboot. If Patching has finished click reboot on Privacy and security.
On restarting your display should be accelerated.
Note; I used OCLP 2.2 and it failed to run as it could not run with root permissions, but 0.62 did all needed.
You can look at the Config and see what i used and remember that serial is for installation, change it after words if you need to go with iCloud.
This EFI could work on another Ventura build higher than 13.0, but i didn't test it since when i tested it with 13.6, the drivers failed to load correctly.
What works.
Graphics with acceleration (suprising my Firefox was working well!), Intel Wireless works, Bluetooth works as seen from the images added, the Mighty
Apple mouse makes the machine move and fell really cool, SD card works, Sound works, Basically many things work, except....
What is not working, 
Camera is not detected
Airdrop is expected not to be working.
In a nutshell, the machine first run Monterey, then changed its SMBios to MacBookPro15,3, threw in all boot-args shown above, but to make the same EFI
switch to Venturen you must change Intel driver and use Ventura driver and bluetooth. All the files in EFI work with Ventura. 
You can see the Pictures included for evidence.
