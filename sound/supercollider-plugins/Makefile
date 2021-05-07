#
# Copyright (C) 2007-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=supercollider-plugins
PKG_VERSION:=3.11.1
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0-or-later
PKG_SOURCE:=sc3-plugins-$(PKG_VERSION)-Source.tar.bz2
PKG_SOURCE_URL:=https://github.com/supercollider/sc3-plugins/releases/download/Version-$(PKG_VERSION)/
PKG_HASH:=skip
PKG_BUILD_DIR:=$(BUILD_DIR)/sc3-plugins-$(PKG_VERSION)-Source
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/supercollider-plugins
  SECTION:=base
  CATEGORY:=Sound
  DEPENDS:=supercollider
  TITLE:=SuperCollider sc3-plugins
  URL:=https://www.jackaudio.org/
  MAINTAINER:=Przemysław Rozwałka
endef


define Package/supercollider-plugins/description
Community plugins for SuperCollider
endef


TARGET_CFLAGS += $(FPIC)

CMAKE_OPTIONS += -DCMAKE_BUILD_TYPE=Release -DSUPERNOVA=OFF

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
endef

define Package/supercollider-plugins/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/share/SuperCollider
	$(CP) $(PKG_INSTALL_DIR)/usr/share/SuperCollider/* $(1)/usr/share/SuperCollider/
endef

$(eval $(call BuildPackage,supercollider-plugins))