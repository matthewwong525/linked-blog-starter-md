
# To everyone who's asking about root.

[

News / Method

](https://www.reddit.com/r/androidroot/?f=flair_name%3A%22News%20%2F%20Method%22)

# Introduction

**Skip any section you don't want to know about**

This post will clear any doubts or questions about root. if not comment down.

Any comment containing the question which is pre-answered in this post would be ignored.

# Root origin

## What is root?

Root or generally refered to user (0) is a Linux Kernel user who has set of permissions exceeding any other user within the running operating system.

**Why Linux?**

Well, this question goes deep beyond this post's domain but the simpliest answer is,

The creator of Android [ running in all mobiles except ios and keypad ones ] had thought to use the Linux kernel which is already open source since he didn't have intrest to develop his own.

Thus, All Android devices run on Linux Kernel.

### Root, A unrestricted user

Root as mentioned has unlimited powers to a point he could wipe entire device files and no one would stop him. [ Although not a case in Android since Android Linux kernel is a modified one. ]

Root (or) Super-User (or) Power-user (or) Privileged user are all same and it simply refers to a user who's running under user id 0. As per linux kernel, this user is unrestricted and he could perform any operation.

In normal Android devices this user isn't available by default but in any other Linux, it is. This user is removed as to restrict unknown usage of root which could potentially damage system as many **Android users yet don't know how Powerful a root session is.**

_**The su binary is usually thought to be superuser binary which is absolutely wrong, it's set user.**_

## What's rooting in Android?

Rooting simply means adding user 0? No.

The user 0 isn't removed completely, the so called root user exists in Android, the only difference is we can't run as that user.

So rooting would simply mean a method to run as superuser? you could say yes.

Rooting simply places a file, the so called su binary into your /system/bin folder in Android versions lower than 4.3.

But the case shifted after 4.3, the reason is because the developer [ Current ones of Android, Google Inc ] introduced an new bit of security enhancements which prevented the su binary from working which executed `setuid(0) and setgid(0)` system calls from setuid and setgid bits.

BTW, this enhancements is mentioned [here](https://source.android.com/security/enhancements/enhancements43)

Upon this enhancements, the root method adapted and changed to run from init process as uid 0.

The rooting process does do this now.

Now what's init? let's see that below.

## Init

Init is a program launched by Bootloader which is first program launched by Kernel [ Any. ]

So what's exactly init?

Init [ Initalise ] is a program designed for Linux by the kernel which launches all basic functions for os to boot and work.

The init program sets file permissions, launches daemons that monitor devices, create folders and files, mount folders and partitions, patch rootfs and make sure everything is set properly.

## Init in rooting

So as you know basic of what init is, what's that init will do in rooting?

So advance rooting methods run thier program as root and in turn give other processes root.

How so?

well notice that i mentioned init launches daemons and basically they can launch any program which have proper selinux user and permissions and it will launch program with the user and group specified. Thus setting root binary to launch once isn't sufficient.

That's why rooting methods such as magisk patch init files to run their daemon which provides root as root from init.

[ Daemon -> These are the processes that run with no controlling terminals and usually daemons are designed to never end. ]

# Root? Should i?

Now to main question. Should i root?

first lets view disadvantages than advantages.

## Disclaimers.

- Rooting device is merely your own choice, the result is neither mine or the manufacturers or Developer of root is liable for any damage
    
- You have voided your warrenty [ Ignore if voided already ]
    
- People usually mention security risks, don't believe it, I'll detail why below.
    

Security risks is true if you grant root to unnecessary apps, they can simply destroy device to a point it can't even recover anymore.

After all with great power comes great responsibility

- sudo
    

# Disadvantages

- As root user, if you ever mess up, it's all your responsibility to fix it.
    
- Personally i never faced it even tho i messed up device to the worst condition, People usually say your device may hard brick
    
- Banking apps won't work, Recently some apps are detecting root even with Magisk. [ Eg: ICICI, Axis, SBI etc ]
    
- Bootloops are common but these modules ensure you're safe, so first flash them:
    

- Magisk Bootloop Protector
    
- SystemUI Bootloop Protector
    

- Rooting process if messed, Although can be fixed, it can be tuff for begginer.
    

# Advantages

- What do you expect? You got Privileged permissions such as admin in windows in your mobile, be happy.
    
- You can grant apps Su and they'll do great job to you
    
- You can tweak kernel= great performance for games
    
- You can ban ads from device completely.
    
- You can uninstall unnecessary apps, i mean system apps.
    
- You can perform much more super enjoying tasks, they all can't be listed here.
    

# Recommendations?

Personally, i recommend 100%.

# How to?

- First get magisk.apk and rename to magisk.zip
    
- Now get your device twrp.img
    
- Check steps for your device bootloader unlock.
    

**Don't execute unnecessary fastboot commands.**

- Unlock bootloader
    
- Flash twrp.
    

`fastboot flash recovery twrp.img`

- Reboot to recovery
    
- Wipe data and format it
    
- Copy magisk zip from pc to device.
    

`adb push /path/to/magisk.zip /sdcard/`

- Click flash zip
    
- Flash magisk.zip
    
- clear and format data again
    
- reboot.
    
- Open magisk app, update and follow any steps if mentioned.
    

**Enjoy however this method isn't recommend by developer although being easy.**

**Recommended Method:**

- Open pc, get device drivers and twrp.img for device
    
- Now unlock bootloader
    
- Flash twrp.img and reboot to recovery
    
- Open twrp terminal
    
- Execute these commands:
    

dd if=/dev/block/by-name/boot of=/sdcard/boot.img

If it gives error

cp $(readlink -f /dev/block/by-name/boot) /sdcard/boot.img

If still error persists, check to extract boot.img for your device and extract it.

- Now install magisk.apk
    
- Select patch image
    
- choose the boot.img you extracted
    
- Once process ends, copy it to pc
    
- launch pc and terminal in pc and run
    

adb reboot bootloader

fastboot flash boot /path/to/copied_and_patched/boot.img

- Reboot into os
    
- Open magisk app, if any steps are mentioned follow it.
    

## Pre requisite:

Must have usb debugging enabled

Charged to 80% or more

Must have device drivers [ if windows ]

Understand fastboot and adb commands since they can do anything to device far worse than root or equal to.

## Safetynet, what is it and how to secure?

Safetynet attestation test is a very crucial part of defending against root.

With start of Magisk version 24 and above, Magisk has officially dropped support for Safetynet and Magisk hide, but why is it needed?

Well the most basic root check is the integrity verification which checks any system modifications done, this can be done without root or elevated permission? No.

But privileged application [ located in /system/priv-app and /vendor/priv-app and in /system_ext/priv-app/ ] are having enough rights registered in their permission files which are located in the parent folder but in etc.

Google services and such apps by Google are one such privileged application that can perform pretty tasks.

They will report a Safetynet failure under condition that either a system modification is detected or root is.

Thus, a safety net failure can result in apps not launching or blocking or detecting root, thus with Magisk 24 starting, people thought safetnet fix is best use.

**Right now, this module is no longer needed, now safetynet is fixed by adding Google play services and Google play store to denylist. Using the module would cause trouble to safetynet.**

**The best way to detect magisk risks are using momo.apk and magiskdetector.apk and yasnac is best safetynet test, it even provides reason of safetynet failure**

# Additional Information

**What's This Section?**

This section is as important as above.

This section deals with many useful information and guiides for root users which cannot be mentioned here due to words limit by reddit post (40000 characters)

Follow links to learn them.

- [Credits](https://www.reddit.com/r/androidroot/comments/vr812f/to_everyone_whos_asking_about_root/iexikgs?utm_medium=android_app&utm_source=share&context=3)
    
- [Post rooting tasks](https://www.reddit.com/r/androidroot/comments/vr812f/to_everyone_whos_asking_about_root/ieuftrl?utm_medium=android_app&utm_source=share&context=3)
    
- [Selinux](https://www.reddit.com/r/androidroot/comments/vr812f/to_everyone_whos_asking_about_root/ieu16du?utm_medium=android_app&utm_source=share&context=3)
    
- [Codenames](https://www.reddit.com/r/androidroot/comments/vr812f/to_everyone_whos_asking_about_root/iewtz08?utm_medium=android_app&utm_source=share&context=3)
    
- [Quick Module Management](https://www.reddit.com/r/androidroot/comments/vr812f/to_everyone_whos_asking_about_root/iewvw1e?utm_medium=android_app&utm_source=share&context=3)
    
- [Bootloops](https://www.reddit.com/r/androidroot/comments/vr812f/to_everyone_whos_asking_about_root/if3oic0?utm_medium=android_app&utm_source=share&context=3)
    
- [Commands](https://www.reddit.com/r/androidroot/comments/vr812f/to_everyone_whos_asking_about_root/if408ql?utm_medium=android_app&utm_source=share&context=3)
    

**More to be added.**

### End

Thanks for reading

Csral @github