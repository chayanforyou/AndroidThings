## Booting Androidthings on RaspberryPi3

Download the prebuilt image from [here](https://dl.google.com/dl/androidthings/rpi3/devpreview/1/androidthings_rpi3_devpreview_1.zip) or [here](https://media.githubusercontent.com/media/chayanforyou/AndroidThings/master/androidthings_rpi3_devpreview_1.zip)

Using command line `wget -c https://dl.google.com/dl/androidthings/rpi3/devpreview/1/androidthings_rpi3_devpreview_1.zip`

unzip `androidthings_rpi3_devpreview_1.zip`

this will unzip and create `iot_rpi3.img` image which we need to install on SD card.

`sudo dd bs=1M if=./iot_rpi3.img of=/dev/sdb`

where `/dev/sdb` is assumed to be device name of SD card which we needs to connect to Raspberry Pi.
This will flash the image on SD card, and create 5 partitions like below as seen using mount command on desktop,

mount

`
/dev/sdb11 on /media/myuser/oem type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb6 on /media/myuser/_ type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1 on /media/myuser/RPIBOOT type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdb13 on /media/myuser/gapps type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb15 on /media/myuser/data type ext4 (rw,nosuid,nodev,uhelper=udisks2)
`

Now, Put the SD card to RPi and connect the ethernet cable to RPi. Once power is connected, Androidthings will boot and stop at the launcher which displays “Androidthings” logo / text and at footer will show the Ethernet IP address, in our case it was 192.168.1.101

Now, on desktop install adb as,

`$ sudo apt-get install android-tools-adb`

Connect Adb to Androidthings RPi,

`$ adb connect`

This will connect the adb, now use adb shell to login to shell

`$ adb shell`

To connect to Wifi, follow steps from https://developer.android.com/things/hardware/raspberrypi.html#connecting_wi-fi

More reference : https://developer.android.com/things/sdk/index.html
