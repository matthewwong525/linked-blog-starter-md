_**This section deals with what to do after rooting?**_

# Precautions

- Never grant root to unnecessary apps.
    
- Don't flash or run unnecessary modules and scripts
    

# Modules

_**There are some very important modules to be flashed for own safety, first flash these then any other.**_

- [Magisk Bootloop Protector](https://github.com/Magisk-Modules-Alt-Repo/HuskyDG_BootloopSaver/releases)
    

- Please make sure you grant it to patch bootimg and enable new safemode. To do so, create a file new_safemode in below mentioned paths or simply execute the command below.
    

# Paths: /cache, /data/unencrypted, /metadata, /persist, /mnt/vendor/persist

# command is below

for dir in /cache /data/unencrypted /metadata /mnt/vendor/persist /persist; do touch $dir/new_safemode; done

- [SystemUI Bootloop Protector](https://github.com/tsukimio/systemui-bootloop/releases)
    

- This is a completely optional module.
    

# Granting Superuser

Remember granting super user is a highly affecting situation, so please do remember what app you're granting and for what?

# Must have root apps.

Firstly get yourself a file manager, I really recommend [this](https://github.com/zhanghai/MaterialFiles/releases)

Now get a terminal, i recommend [Termux](https://f-droid.org/en/packages/com.termux/)

Inside termux execute this command:

pkg upgrade && pkg update ; pkg install tsu curl wget zip binutils tar proot fakeroot zsh git termux-api ; termux-setup-storage ; su -c echo "Done" && return 0

Now get Terminal Emulator from playstore and grant it su.

Now install Vanced Manager, remember only trust apkmirror site to get third party root apps, The other site is official github.

[Vanced](https://www.apkmirror.com/apk/team-vanced/vanced-manager/)

# Ad Blocking

Now, finally run these set of commands but first remove or don't enable the systemless hosts module in magisk.

Now:

first download this file:

# In termux:

curl -L https://raw.githubusercontent.com/jerryn70/GoodbyeAds/master/Hosts/GoodbyeAds.txt -o hosts && su

mount -o remount,rw /dev

mount -o remount,rw / && mount -o remount,rw /system 2> /dev/null

mount -o remount,rw /system/etc/hosts 2> /dev/null

cp ./hosts /etc/hosts

# if error, try

cat ./hosts < /etc/hosts

mount -o remount,ro /system/etc/hosts && mount -o remount,ro /

mount -o remount,ro /system 2> /dev/null

mount -o remount,ro /dev

reboot

Now ads are blocked if the host file has the content of goodbye ads.

# Magisk

**Note that if you keep getting reboot to recovery warning more than trice, ignore it from next time by clicking cancel or anywhere on screen**

Open magisk and follow these steps:

- Open Magisk
    
- Open settings [ Top right of magisk ]
    
- scroll and enable Zygisk
    
- Reboot
    
- Go back and enable denylist
    
- Reboot
    
- Now deny all those apps mentioned below.
    

- All your banking apps and apps that Don't need root and apps that aren't modules.

- Google play store, Google play services, Google play ar service, Google, Google play games, Carrier services, Google play protect services, Google services framework and google support services

- Now reboot
    
- Enable bio-metric auth [ Must have password and fingerprint on device. ]
    
- Set timeout to 15 seconds
    
- Ensures superuser toast is enabled.
    
- All set.
    

# Must Have Modules

Some of the modules are a must have for enjoying root.

_**Don't take riru version for any module below, download and install only zygisk version.**_

**Lsposed works with xposed modules**

- [Lsposed](https://github.com/LSPosed/LSPosed/releases)
    
- [Magisk hide props config](https://github.com/Magisk-Modules-Repo/MagiskHidePropsConf/releases)
    

# End

Now enjoy your new rooted device as you want with all that modules you want!

Have fun.