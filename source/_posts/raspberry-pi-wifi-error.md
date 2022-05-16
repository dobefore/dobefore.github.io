---
title: raspberry-pi-wifi-error
readmore: true
date: 2022-05-16 08:43:15
tags:
- raspberry-pi
- wifi
---

On raspberry pi 4b,two reasons cause wifi error.

## usb 3.0 interfere with wifi

reproduce:

```none
sudo wpa_supplicant  -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
pplicant.conf 

Successfully initialized wpa_supplicant
wlan0: Trying to associate with SSID 'SZMIFI'
wlan0: CTRL-EVENT-ASSOC-REJECT bssid=00:00:00:00:00:00 status_code=16
wlan0: Trying to associate with SSID 'SZMIFI'
wlan0: CTRL-EVENT-ASSOC-REJECT bssid=00:00:00:00:00:00 status_code=16
wlan0: Trying to associate with SSID 'SZMIFI'
wlan0: CTRL-EVENT-ASSOC-REJECT bssid=00:00:00:00:00:00 status_code=16
wlan0: Trying to associate with SSID 'SZMIFI'
wlan0: CTRL-EVENT-ASSOC-REJECT bssid=00:00:00:00:00:00 status_code=16
wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="SZMIFI" auth_failures=1 duration=10 reason=CONN_FAILED
wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="SZMIFI"
wlan0: Trying to associate with SSID 'SZMIFI'
wlan0: CTRL-EVENT-ASSOC-REJECT bssid=00:00:00:00:00:00 status_code=16
wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="SZMIFI" auth_failures=2 duration=20 reason=CONN_FAILED
^Cnl80211: deinit ifname=p2p-dev-wlan0 disabled_11b_rates=0
p2p-dev-wlan0: CTRL-EVENT-TERMINATING 
nl80211: deinit ifname=wlan0 disabled_11b_rates=0
```



fix: switch to usb 2.0

## HDMI is jamming its own wifi

screen definition higher than 1920*1080 will cause wifi stop working.

fix:keep screen definition to 1920*1080 and apply,in the Preference->Screen Configuration

## keyboard and mouce sometimes dont respond.

fix: disable hdmi until raspberry pi boot with keyboard and mouce

## Reference

- https://hackaday.com/2019/11/28/raspberry-pi-4-hdmi-is-jamming-its-own-wifi/