# Raspberry-Pi-RTC1307
# How to RTC Setup

service ntp stop
insserv -r ntp

vi /etc/rc.local
echo ds1307 0x68 > /sys/class/i2c-adapter/i2c-1/new_device
sleep 3
hwclock -s

vi /etc/modules
i2c-dev
rtc-ds1307

reboot
dmesg|grep 1307

apt-get install ntpdate
ntpdate time.nist.gov
date
timedatectl status
hwclock -w


