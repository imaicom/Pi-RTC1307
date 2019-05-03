# Raspberry-Pi-RTC1307
# How to RTC Setup
# RTC1307 module on 1-3-5-7-9 pin 

raspi-config
# 9 Advanced Options -> A7 I2C -> Enabled YES
# Restart to be able to use the I2Cbus


apt-get install i2c-tools
i2cdetect -y 1

service ntp stop
insserv -r ntp
# NTP does not excute at the same time as RTC

vi /etc/rc.local
# To add to the line above the "exit 0"
 echo ds1307 0x68 > /sys/class/i2c-adapter/i2c-1/new_device
 sleep 3
 hwclock -s

vi /etc/modules
 i2c-dev
 rtc-ds1307

reboot
dmesg|grep 1307
i2cdetect -y 1

apt-get install ntpdate
ntpdate time.nist.gov
date
timedatectl status
hwclock -w
timedatectl status

ntpdate -s -b ntp.jst.mfeed.ad.jp
