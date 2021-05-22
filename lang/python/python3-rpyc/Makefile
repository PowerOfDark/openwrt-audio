include $(TOPDIR)/rules.mk

PKG_NAME:=python3-rpyc
PKG_VERSION:=5.0.1
PKG_RELEASE:=1

PKG_HASH:=581f14e49781242c34b55f989bec24dd386ff0d5d445b8d972c7e52bd3219112
PKG_SOURCE:=$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/tomerfiliba-org/rpyc/archive/refs/tags/
PKG_MAINTAINER:=Przemysław Rozwałka
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_FIXUP:=patch-libtool
PKG_BUILD_DIR:=$(BUILD_DIR)/rpyc-$(PKG_VERSION)/

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-rpyc
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=RPyC for Python3
  URL:=https://rpyc.readthedocs.io/
  DEPENDS:=+python3-light
endef

define Package/python3-rpyc/description
  Transparent, Symmetric Distributed Computing.
endef


$(eval $(call Py3Package,python3-rpyc))
$(eval $(call BuildPackage,python3-rpyc))
$(eval $(call BuildPackage,python3-rpyc-src))