# Raspberry-Pi-RTC1307

一時的
service ntp stop
恒久的
insserv -r ntp

/etc/rc.local
echo ds1307 0x68 > /sys/class/i2c-adapter/i2c-1/new_device
sleep 3
hwclock -s

/etc/modules
snd-bcm2835
i2c-dev
rtc-ds1307

reboot

dmesg|grep 1307

apt-get install ntpdate
ntpdate time.pref.okayama.jp
hwclock -w


timedatectl status
