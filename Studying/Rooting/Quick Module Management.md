# Quick Module Management

_**This section allows you to delete, disable, enable modules instantly without reboot!**_

To understand how? understand first what they do?

***All modules folders are found in /data/adb/modules/

# Disable

When you disable a module in magisk, it simply places a file disable in module folder.

But why reboot??

Well, the answer is simple, some modules have thier changes already done and rebooting would ensure magisk wouldn't load those modules again and revert thier changes completely!

# Enable

Ofc, just delete the file disable.

# Delete module?

This mostly wouldn't require reboot **unless module Hasn't patched boot.img or has multiple mounts set.**

Simply delete module folder and module is no longer found in magisk app.

Note that, if module have boot.img or other img patched, you either have to manually unpatch them or developer should keep a script placed.

# Skip reboot?

As i mentioned Init starts everything and even Magisk is started by Init and Init is patched by Magisk.

Execute this commands instead of reboot and check if it works, because not all modules are easy to revert thier changes.

su
/init

# End