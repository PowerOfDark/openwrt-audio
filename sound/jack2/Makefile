#
# Copyright (C) 2007-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=jack2
PKG_VERSION:=1.9.18
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0-or-later
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/jackaudio/jack2.git
PKG_MIRROR_HASH:=56fbee2c0e5ed5cd79116361b70ea4610806218e0ba86e2b4413b8d3e254a5b3
PKG_SOURCE_DATE:=2021-04-26
PKG_SOURCE_VERSION:=852ba2b8ebc944865e75d8eb5d4550d408772f3b
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/jack2
  SECTION:=base
  CATEGORY:=Sound
  DEPENDS:=+libpthread +alsa-lib +libavahi-client +libreadline +libdb47 +libsndfile +libsamplerate +libstdcpp +JACK2_USE_DBUS:python3-dbus
  TITLE:=jack2 audio server
  URL:=https://www.jackaudio.org/
  MAINTAINER:=Przemysław Rozwałka
  VARIANT:=base
endef


define Package/jack2/description
	High-performance audio server
endef

define Package/jack2/config
	source "$(SOURCE)/Config.in"
endef

TARGET_CFLAGS += $(FPIC)

CONFIGURE_VARS += \
	CPP="$(TARGET_CROSS)cpp"

CONFIGURE_CMD = ./waf


CONFIGURE_ARGS = \
		--alsa \
		--prefix=/usr \
		--libdir=/usr/lib \
		--bindir=/usr/bin \


ifeq ($(CONFIG_JACK2_USE_DBUS),y)
CONFIGURE_ARGS+= --dbus
endif

CONFIGURE_ARGS:=configure $(CONFIGURE_ARGS)


define Build/Compile
	(cd $(PKG_BUILD_DIR); \
		./waf install -j$(shell nproc) \
		--destdir="$(PKG_INSTALL_DIR)" \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
endef

define Package/jack2/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
	ifeq ($(CONFIG_JACK2_USE_DBUS),y)
	$(INSTALL_DIR) $(1)/usr/share/dbus-1
	$(CP) $(PKG_INSTALL_DIR)/usr/share/dbus-1/* $(1)/usr/share/dbus-1/
	endif
endef

$(eval $(call BuildPackage,jack2))