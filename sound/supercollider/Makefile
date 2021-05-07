#
# Copyright (C) 2007-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=supercollider
PKG_VERSION:=3.11.2
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0-or-later
PKG_SOURCE:=SuperCollider-$(PKG_VERSION)-Source.tar.bz2
PKG_SOURCE_URL:=https://github.com/supercollider/supercollider/releases/download/Version-$(PKG_VERSION)/
PKG_HASH:=c22c32c6bc482671d4fb8f51672df712d97a6a6277235c4da2312910303a0506
PKG_BUILD_DIR:=$(BUILD_DIR)/SuperCollider-$(PKG_VERSION)-Source
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/supercollider
  SECTION:=base
  CATEGORY:=Sound
  DEPENDS:=+alsa-lib +libavahi-client +fftw3f +jack2 +libudev
  TITLE:=SuperCollider
  URL:=https://www.jackaudio.org/
  MAINTAINER:=Przemysław Rozwałka
endef


define Package/supercollider/description
	SuperCollider is a platform for audio synthesis and algorithmic composition, used by musicians, artists, and researchers working with sound.
	It is free and open source software available for Windows, macOS, and Linux.
endef


TARGET_CFLAGS += $(FPIC)

CMAKE_OPTIONS += -DCMAKE_BUILD_TYPE=Release -DSUPERNOVA=OFF -DSC_ED=OFF -DSC_EL=OFF -DSC_VIM=ON \
    -DSC_IDE=OFF -DNO_X11=ON -DSC_QT=OFF -DAUDIOAPI=jack -DSC_ABLETON_LINK=OFF

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
endef

define Package/supercollider/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
endef

$(eval $(call BuildPackage,supercollider))