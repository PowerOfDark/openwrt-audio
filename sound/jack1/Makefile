#
# Copyright (C) 2007-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=jack1
PKG_VERSION:=1.0.0
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0-or-later
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/jackaudio/jack1.git
PKG_SOURCE_DATE:=2021-04-26
PKG_SOURCE_VERSION:=b04083761496410a52126cdbcd35c557ee82f2e5
PKG_MIRROR_HASH:=52dd1007fca8a6e59b7b10f1977f3a2211269b9a7e08718d772ea58f3cfe1a3e
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/jack1
  SECTION:=base
  CATEGORY:=Sound
  DEPENDS:=+alsa-lib +libavahi-client +libreadline +libdb47 +libsndfile +libsamplerate
  TITLE:=jack1 audio server
  URL:=https://www.jackaudio.org/
  MAINTAINER:=Przemysław Rozwałka
endef


define Package/jack1/description
	High-performance audio server
endef


TARGET_CFLAGS += $(FPIC)


define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) DESTDIR="$(PKG_INSTALL_DIR)" install
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
endef

define Package/jack1/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/man
	$(CP) $(PKG_INSTALL_DIR)/usr/man/* $(1)/usr/man/
endef

$(eval $(call BuildPackage,jack1))