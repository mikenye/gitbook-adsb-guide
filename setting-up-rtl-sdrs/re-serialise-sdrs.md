---
description: 'You can skip this step if you''re not using an RTLSDR radio (for example: bladeRF).'
---

# Re-Serialise SDRs

As most RTL-SDRs ship with the same serial number, confusion may be caused if more than one SDR is ever present. It is a good rule of thumb to change your SDR serial numbers to match the frequencies they receive for.

The remainder of this guide assumes that:

* The SDR used for ADS-B Mode-S \(1090MHz\) reception will have a serial number of `00001090`
* The SDR used for ADS-B UAT \(978MHz\) reception \(if used\) will have a serial number of `00000978`.

To set these serial numbers:

Unplug all SDRs, leaving only the SDR to be used for 1090MHz reception plugged in. Issue the following command:

```text
sudo docker run --rm -it --device /dev/bus/usb --entrypoint rtl_eeprom mikenye/readsb-protobuf -s 00001090
```

You should be presented with the following. Your details may differ slightly, however ensure the device's new serial number will be `00001090`. Press `y` to proceed.

```text
Found 1 device(s):
  0:  Generic RTL2832U

Using device 0: Generic RTL2832U
Found Rafael Micro R820T tuner

Current configuration:
__________________________________________
Vendor ID:              0x0bda
Product ID:             0x2832
Manufacturer:           Realtek
Product:                RTL2832U
Serial number:          00001000
Serial number enabled:  yes
IR endpoint enabled:    no
Remote wakeup enabled:  no
__________________________________________

New configuration:
__________________________________________
Vendor ID:              0x0bda
Product ID:             0x2832
Manufacturer:           Realtek
Product:                RTL2832U
Serial number:          00001090
Serial number enabled:  yes
IR endpoint enabled:    no
Remote wakeup enabled:  no
__________________________________________
Write new configuration to device [y/n]? y

Configuration successfully written.
Please replug the device for changes to take effect.
```

Next, if you intend on receiving ADS-B UAT \(978MHz\) data with a second SDR, Unplug all SDRs, leaving only the SDR to be used for 978MHz reception plugged in. Issue the following command:

```text
sudo docker run --rm -it --device /dev/bus/usb --entrypoint rtl_eeprom mikenye/readsb-protobuf -s 00000978
```

You should be presented with the following. Your details may differ slightly, however ensure the device's new serial number will be `00000978`. Press `y` to proceed.

```text
Found 1 device(s):
  0:  Generic RTL2832U

Using device 0: Generic RTL2832U
Found Rafael Micro R820T tuner

Current configuration:
__________________________________________
Vendor ID:              0x0bda
Product ID:             0x2832
Manufacturer:           Realtek
Product:                RTL2832U
Serial number:          00001000
Serial number enabled:  yes
IR endpoint enabled:    no
Remote wakeup enabled:  no
__________________________________________

New configuration:
__________________________________________
Vendor ID:              0x0bda
Product ID:             0x2832
Manufacturer:           Realtek
Product:                RTL2832U
Serial number:          00000978
Serial number enabled:  yes
IR endpoint enabled:    no
Remote wakeup enabled:  no
__________________________________________
Write new configuration to device [y/n]? y

Configuration successfully written.
Please replug the device for changes to take effect.
```

Unplug all SDRs and then plug them back in again to make the system aware of the new serials. A reboot will not do that.

