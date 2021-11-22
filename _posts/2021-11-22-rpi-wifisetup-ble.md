---
title: Setting up Raspberry Pi WiFi via Bluetooth
categories:
- Raspberry Pi
---

You can run a BLE GATT server on a Raspberry Pi machine, through which you can
use other devices (GATT clients) such as a mobile phone to set up the WiFi of 
the Raspberry Pi among other things.

There is a nice example of python RPi GATT server code written by 
[Douglas Otwell](https://github.com/Douglas6/cputemp). Follow the code,
you can create your own GATT server that exposes characteristics that

* receives SSID of the target access point
* receives PSK of the target access point
* shows current IP address of the device as a connection state
* receives a command to trigger restarting of WiFi network

This [repository](https://github.com/snowdayclub/rpi-wifisetup-ble) demonstrates
such case. Clone the repository and copy following files from the [repository above](https://github.com/Douglas6/cputemp):

* advertisement.py
* bletools.py
* service.py

to the directory. Then run the script with root privilege:
```
$ sudo python3 wifisetup.py
```

For the GATT client, you can use [nRF Connect for Mobile](https://play.google.com/store/apps/details?id=no.nordicsemi.android.mcp&hl=en_CA&gl=US).  Scan the RPi
for the name, `RPi WiFi Setup`. Once connected, you can write SSID, PSK for the
target AP, then write any value, e.g. `0x00` to the `Restart WiFi Network`
characteristics. Successfully connected, you can see the IP address of the 
Raspberry Pi by reading `IP Address` characteristic.