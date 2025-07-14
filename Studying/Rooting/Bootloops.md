# Emergency Bootloop

_**Thanks to reports on this community, i almost forgot this very important concept.**_

# What's bootoop

Bootloop as the name says, the booting process will loop. Thus your os returns to recovery or fastboot or boot logo.

This guide will explain all bootloops fix as much as it can.

# Recovery Bootloop

I have personally no clue why this happens but it happened a lot to me.

The only and might the best way to exit this would be forcing bootloader.

Simply hold the bootloader combination of your mobile until your device goes to bootloader [ Fastboot ].

If your device keeps turning on and off, hold the combo until you see your device starting to boot up and leave the combo.

Now you have either 2 options:

- Your device booted directly into os.
    

Done.

- Your device went to fastboot.
    

Simply reboot and done.

# Fastboot Bootloop

One of the most weirdest Bootloop which is also common and easy to fix.

To escape these bootloops, you have two choices.

Easier and best choice is,

As you asked fastboot to help for recovery Bootloop, now ask recovery to return the favour.

I mean, hold down recovery combination until device boots into recovery, in case of multiple reboots, hold down recovery combination until device starts to boot and release.

_**Why i gave second option?**_

Well, there is a chance it wouldn't work, what then?

Hold down fastboot combo and boot into fastboot.

Now simply reboot.

# Bootloop

Now actual bootloop or most common one is the bootloop to boot logo.

Now to fix this, there are multiple causes and multiple ways. Follow below.

## Magisk Module Bootloop

To fix this, we have the best choices,

- The best ever choice is to have [Magisk Bootloop Protector](https://github.com/Magisk-Modules-Alt-Repo/HuskyDG_BootloopSaver/releases) Module installed.
    
- The other way which is best but manual is, safemode
    

Now question is how to boot safemode when in bootloop?

Follow these steps:

Power off your device or reboot it.

When the boot logo, i.e, boot animation appears, Hold down volume up and down keys and dont release them until you hear a vibration from your device.

Now release keys and you're in safemode.

- The other way is using adb to set property persist.sys.safemode as 1
    

setprop persist.sys.safemode 1 && reboot.

Alternatively, using recovery file manager or echo add entry

persist.sys.safemode=1 in /system/build.prop

**make sure that entry is wiped over next reboot, else you can't exit safemode but a reboot from safemode should generally wipe this entry. If not, do it yourself.**

## Magisk Boot Image

This is not quite common but here is what to do.

Simply flash stock boot.img

If no stock image is available with you or you can't get a copy, get magisk.apk, rename it to magisk.zip

Copy it to your mobile, rename it to uninstall.zip

Flash it.

Done.

## Kernel Panic

Comeon, even kernel panics when there is an important file for it to be loaded to boot device is missing.

Such as init scripts, init itself or system images, some other files or boot scripts etc.

The easiest way is to record kernel logs and solve yourself since Kernel panics for many reasons.

## Missing system files or deleted accidentally.

Wipe all partitions and format data in recovery

Re-Flash whatever rom you're using even if its stock.

Wipe and flash data again.

Reboot.

## System misconfiguration

Find the misconfiguration and fix it since i can't predict what could misconfigure.

# End