# android_hardware_wifi_realtek_drivers_8822bu

This is the linux driver for an AC 1200 Dual-Band USB 3.0 Wi-Fi Adapter. ([Amazon](https://www.amazon.com/gp/product/B075D8SHJ9/ref=oh_aui_detailpage_o00_s00))

The original repo was forked and edited so that it would compile on Ubuntu 17.04  4.10.0-33-generic, and use DKMS



#### Get your VendorID:DeviceID
```bash
$ lsusb | grep -i real
Bus 003 Device 002: ID 0bda:b812 Realtek Semiconductor Corp.
```

#### Download
```bash
$ sudo apt update
$ sudo apt install linux-headers-generic build-essential git
$ git clone https://github.com/ottov/android_hardware_wifi_realtek_drivers_8822bu.git
```

#### Verify your VendorID & Device ID are in this driver (optional)
```bash
$ cd android_hardware_wifi_realtek_drivers_8822bu
$ grep -Ri 0bda
rtl8822BU/os_dep/linux/usb_intf.c:#define USB_VENDER_ID_REALTEK           0x0BDA

$ grep -Ri b812
os_dep/linux/usb_intf.c: {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB812, 0xff, 0xff, 0xff),.driver_info = RTL8822B},
```

#### Test no errors during compile (optional)
```bash
$ cd rtl8822BU
$ make
$ make clean
```

#### Install using DKMS, reboot
```bash
$ sudo apt install dkms
$ cd android_hardware_wifi_realtek_drivers_8822bu
$ sudo dkms add ./rtl8822BU
$ sudo dkms install rtl8822BU/5
$ sudo reboot
```

