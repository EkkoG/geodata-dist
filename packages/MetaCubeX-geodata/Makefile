# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2021-2022 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=v2ray-geodata
PKG_RELEASE:=1

PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Tianling Shen <cnsztl@immortalwrt.org>

include $(INCLUDE_DIR)/package.mk

GEOIP_VER:=20240105160342
GEOIP_FILE_HASH:=d4aed7e49ee6b49fbace1fc3890482606a2d7e44317887cf6322e257d88301a3
GEOIP_FILE:=geoip.dat
define Download/geoip
  URL:=https://github.com/MetaCubeX/meta-rules-dat/raw/release/
  URL_FILE:=geoip.dat
  FILE:=$(GEOIP_FILE)
  HASH:=$(GEOIP_FILE_HASH)
endef

GEOSITE_VER:=20240109160346
GEOSITE_FILE_HASH:=3ede629c4e91ad18de62e527d333c89e26ec350da454541505fec6eca9f252ef
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
