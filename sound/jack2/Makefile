#
# Copyright (C) 2007-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=jack2
PKG_VERSION:=3.3.8
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0-or-later
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/jackaudio/jack2.git
PKG_MIRROR_HASH:=97f0da871749a159a1024f5472a8b34b9b43971fd2839badae50c94efcab35e4
PKG_SOURCE_DATE:=2021-04-26
PKG_SOURCE_VERSION:=852ba2b8ebc944865e75d8eb5d4550d408772f3b
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/jack2
  SECTION:=base
  CATEGORY:=Sound
  DEPENDS:=+libpthread +alsa-lib +libavahi-client +dbus +libreadline
  TITLE:=jack2 audio server
  URL:=http://www.fftw.org/
  MAINTAINER:=Przemysław Rozwałka
endef


define Package/jack2/description
	High-performance audio server
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

define Package/jack1/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/man
	$(CP) $(PKG_INSTALL_DIR)/usr/man/* $(1)/usr/man/
endef

$(eval $(call BuildPackage,jack2))