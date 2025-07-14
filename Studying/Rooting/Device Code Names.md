# Device Codenames

_**This section deals with device uniqueness**_

You must have encountered codename atleast once, for example certain modules run only for certain device.

To confirm if they are running in the device they support, shell script isn't a launguage or application to provide such facilities.

Thus, they verify something called device codename.

For example my Redmi note 8 is known to be Ginkgo.

# Why codenames

Codenames are really important than you think, even for rom swapping or twrp installation.

How so? well,

- Codenames make devices unique, No 2 devices holds same codenames
    
- They make devices easier to sort out
    
- They reduce hastle, for example Redmi note 8 and Redmi note 8 Pro has different codenames.
    

# What's my codename?

Your codename is registered in properties.

Execute below command

getprop ro.product.device

# The below output must match above

getprop ro.product.name

# If it didn't, that means some module have renamed your properties, this doesn't cause any damage.
# In most of the times, the original codename is the first output.

# Confirmation

getprop ro.product.system.device

# Here is my config:

# ro.product.system.brand=Xiaomi
# ro.product.system.device=ginkgo
# ro.product.system.manufacturer=Xiaomi
# ro.product.system.model=Redmi Note 8
# ro.product.system.name=aosp_ginkgo

# Some pixel modules modify codename in all ways!

# Risks?

Yes, modifying codename is certainly a risk.

Consider flashing a new rom, if your codenames doesn't match, the TWRP or any recovery would throw a warning saying that codenames doesn't match to registered domain.

Eg:

Your device Codename -> xgx Your modified codename -> xig

Now you try to flash a rom for xgx and recovery throws error claiming that the rom for codename xgx can't be installed for xig.

_**Don't dare to flash xig rom, it'll cause a lot of issues. The codename and seperate roms and modules for codenames is not made for fun.**_

However **Remember that the codename modification done by Magisk module wouldn't persist in recovery.**

Reason?

**Because Magisk isn't active on recovery and neither are modules booted!**

Consider flashing a module, It's same case.

# How to change codename?

_**Since codenames are properties, some properties such as these are readonly.**_

Eg:

# to set properties- setprop <prop> <val>

setprop ro.product.name sus

Failed to set property 'ro.product.name' to 'sus'.
See dmesg for error reason.

**I'll detail what dmesg is in later sections!**

So, how to change codenames?

One method is to do it from Pitch Black Recovery, It has a option to change codenames.

Other is module.

Why is thier no other way? well because, the configuration of ro.product.device and ro.product.name isn't available in properties files.

Since recovery is easy, you can try it. Here is how to do it with module.

Launch termux: and execute below commands

# Termux

su
cd /data/adb/modules/

mkdir Codename_Changer/
cd Codename_Changer/

echo "id=Codename_Changer\nname=Codename Modifier\nversion=v1.0\nversionCode=10000\ndescription=Just my module xD" >> module.prop

echo "ro.product.device=<codename>\nro.product.name=<codename>\nro.product.system.device=<codename>" >> system.prop

# Note that above angular brackets aren't needed.

reboot

# The codename must have changed by next boot!

# Below is a one line command which does same.

su -c 'cd /data/adb/modules/ && mkdir Codename_Changer ; cd Codename_Changer ; echo "id=Codename_Changer\nname=Codename Modifier\nversion=v1.0\nversionCode=10000\ndescription=Just my module xD" >> module.prop && echo "ro.product.device=<codename>\nro.product.name=<codename>\nro.product.system.device=<codename>" >> system.prop ; echo "Device will reboot in 5 seconds. Press ctrl + c to cancel." ; sleep 5 && reboot'

To undo changes, please uninstall module from magisk or delete the folder at /data/adb/modules/Codename_Changer and reboot.

# End