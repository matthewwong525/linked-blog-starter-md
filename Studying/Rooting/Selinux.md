### Selinux

Security-Enchanced Linux is a security enhancement to linux that will verify a set of additional information about the group you belong to and the user you are and what content are you accessing and how much access do you have to it.

Many Linux distributions have adopted selinux and so has Android.

The selinux is set to be enabled by default, please verify if its actually enabled or it'll cause you trouble.

When selinux is disabled in Android, even installing an app is particularly dangerous, only disable selinux for debugging. if you belive you haven't disabled selinux and is disabled by an application, instantly enable selinux and revoke root permissions for all applications.

### Why?

Selinux is good enough for preventing dangerous things happening to device and having it disabled, even a normal app without root would be potentially dangerous.

### How to verify.

Firstly, The basic thing to do as a rooted user is have atleast 2 Terminals, one spare and other main.

I personally use and recommend Termux as main and Terminal Emulator as alternative in emergency.

Open any terminal and execute these set of commands:

# Note that any sentence starting with # is a comment
# and you can ignore it and so will any shell.

su -c getenforce

# The output must be Enforcing
# If its not, then execute below command

su -c setenforce 1

# And recheck enforcement status.

# Now revoke all root permissions granted, alternatively delete file /data/adb/magisk.db

# Now reboot and you'll be fine.