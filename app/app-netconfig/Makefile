#
# Copyright (c) 2015-2021 Dirk Brenken (dev@brenken.org)
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=app-netconfig
PKG_VERSION:=1.0.0
PKG_RELEASE:=1
PKG_LICENSE:=GPL-3.0-or-later
PKG_MAINTAINER:=Przemysław Rozwałka

include $(INCLUDE_DIR)/package.mk

define Package/app-netconfig
	SECTION:=base
	CATEGORY:=App
	TITLE:=App network config
	PKGARCH:=all
endef

define Build/Prepare
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/app-netconfig/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/etc/init.d/* $(1)/etc/init.d/
endef

$(eval $(call BuildPackage,app-netconfig))