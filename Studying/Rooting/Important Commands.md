# Important Commands

**This posts issues some of the important commands for Android.**

- Get currently running app
    

# This command gives package of what app is open on screen

su -c "dumpsys window windows | grep -E 'mCurrentFocus|mFocusedApp|mInputMethodTarget|mSurface' | grep -v 'ScreenDecorOverlay' | grep -v 'systemui' | grep -v 'mAnimationIs' | grep -v 'NavigationBar' | grep -v 'Toast' | grep -v 'StatusBar' | cut -d '/' -f 1 | cut -d '(' -f 2 | cut -d '=' -f 2"

- Watch boot animation without rebooting
    

su -c bootanimation

- Reboot to safe mode
    

su -c "setprop persist.sys.safemode 1 && reboot"

- Make device completely unlocked and modify-able
    

_**Warning: Having device completely write accessed is highly security risk. Do lock everything as soon as you can.**_

su -c "mount -o remount,rw /; mount -o remount,rw /dev ; mount -o remount,rw /system ; mount -o remount,rw /vendor ; mount -o remount,rw /system/etc/hosts ; mount -o remount,rw /system/etc/init ; mount -o remount,rw /system/etc/init/hw/init.rc ; mount -o remount,rw /data ; mount -o remount,rw /cache ; mount -o remount,rw /config ; echo 'Remounted whole system. Please remember that the system would be un-mounted to previous state and a warning would be logged that the device will reboot. \nTime for that task is 900 Seconds [ 15 Mins ].' && sleep 900 && mount -o remount,ro /; mount -o remount,ro /dev ; mount -o remount,ro /system ; mount -o remount,ro /vendor ; mount -o remount,ro /system/etc/hosts ; mount -o remount,ro /system/etc/init ; mount -o remount,ro /system/etc/init/hw/init.rc ; mount -o remount,ro /data ; mount -o remount,ro /cache ; mount -o remount,ro /config ; echo '! Device will reboot for Security purposes.\nTime for reboot: 30s' && sleep 30 && reboot" 2> /dev/null

- Launch all apps installed in system
    

_**Idk why you would want to do this, maybe prank or anything but it's too hard to stop once started.**_

for pkg in /data/data/*; am start $(cmd package resolve-activity --brief -c android.intent.category.LAUNCHER $(echo $pkg | cut -d "/" -f 4) | tail -1); done

# End