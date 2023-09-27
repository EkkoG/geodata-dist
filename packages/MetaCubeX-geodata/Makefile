# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2021-2022 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=v2ray-geodata
PKG_RELEASE:=1

PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Tianling Shen <cnsztl@immortalwrt.org>

include $(INCLUDE_DIR)/package.mk

GEOIP_VER:=20230922160349
GEOIP_FILE_HASH:=3498e4b8b9b60e1019dfc62df6cfa3aaaef010712a4a56d788c0f11eda417791
GEOIP_FILE:=geoip.dat
define Download/geoip
  URL:=https://github.com/MetaCubeX/meta-rules-dat/raw/release/
  URL_FILE:=geoip.dat
  FILE:=$(GEOIP_FILE)
  HASH:=$(GEOIP_FILE_HASH)
endef

GEOSITE_VER:=20230927160357
GEOSITE_FILE_HASH:=3304d0e00a366695c7ce7554545f99daccd9d603b074a2f8e29ed4f60eac6398
GEOSITE_FILE:=geosite.dat
define Download/geosite
  URL:=https://github.com/MetaCubeX/meta-rules-dat/raw/release/
  URL_FILE:=geosite.dat
  FILE:=$(GEOSITE_FILE)
  HASH:=$(GEOSITE_FILE_HASH)
endef

define Package/v2ray-geodata/template
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=IP Addresses and Names
  URL:=https://www.v2fly.org
  PKGARCH:=all
endef

define Package/v2ray-geoip
  $(call Package/v2ray-geodata/template)
  TITLE:=GeoIP List for V2Ray
  VERSION:=$(GEOIP_VER)-$(PKG_RELEASE)
  LICENSE:=CC-BY-SA-4.0
endef

define Package/v2ray-geosite
  $(call Package/v2ray-geodata/template)
  TITLE:=Geosite List for V2Ray
  VERSION:=$(GEOSITE_VER)-$(PKG_RELEASE)
  LICENSE:=MIT
endef

define Build/Compile
endef

define Package/v2ray-geoip/install
	$(INSTALL_DIR) $(1)/usr/share/v2ray
	$(INSTALL_DATA) $(DL_DIR)/$(GEOIP_FILE) $(1)/usr/share/v2ray/geoip.dat
endef

define Package/v2ray-geosite/install
	$(INSTALL_DIR) $(1)/usr/share/v2ray
	$(INSTALL_DATA) $(DL_DIR)/$(GEOSITE_FILE) $(1)/usr/share/v2ray/geosite.dat
endef

$(eval $(call Download,geoip))
$(eval $(call Download,geosite))
$(eval $(call BuildPackage,v2ray-geoip))
$(eval $(call BuildPackage,v2ray-geosite))
