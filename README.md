# Systemd service to change mac address after boot

This systemd service will change a device's mac address everytime it boots.
Useful when devices with same mac address need to be access on LAN. (Happens
when the wireless chip is by the same manufacturer with the same part number).

Use this with mDNS to easily access a device over ssh with a modified mac
address.

## Install 

```
sudo apt install macchanger net-tools isc-dhcp-client
cd /path/to/macacetamol
sudo cp changemac.service /etc/systemd/system/
sudo sed -i -E "s|ABS_PATH|$(pwd)/change_mac|g" /etc/systemd/system/changemac.service
sudo systemctl enable changemac
sudo systemctl start changemac
```
