v2ray-like geodata feed for OpenWrt

## Add by script

Pick one of the source you want to add, and run it

```bash
sh -c "$(curl https://raw.fgit.cf/EkkoG/openwrt-dist/master/add-feed.sh)" -- geodata/v2ray
sh -c "$(curl https://raw.fgit.cf/EkkoG/openwrt-dist/master/add-feed.sh)" -- geodata/Loyalsoldier
sh -c "$(curl https://raw.fgit.cf/EkkoG/openwrt-dist/master/add-feed.sh)" -- geodata/MetaCubeX
```

## Install

```bash
opkg update
opkg install geoip-v2ray
opkg install geosite-v2ray
```
