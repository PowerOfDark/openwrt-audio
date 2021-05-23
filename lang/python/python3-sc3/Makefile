include $(TOPDIR)/rules.mk

PKG_NAME:=python3-sc3
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_HASH:=e7754bf0864fc2794a005f738ba4fbdc43b2f03f738c134164d7373203167f2a
PKG_SOURCE_VERSION:=2dd3edb5c1df64ea619cf01ae3978acde7231355
PKG_SOURCE:=$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/smrg-lm/sc3/archive/
PKG_MAINTAINER:=Przemysław Rozwałka
PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE
PKG_FIXUP:=patch-libtool
PKG_BUILD_DIR:=$(BUILD_DIR)/sc3-$(PKG_SOURCE_VERSION)/

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-sc3
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=SC3 for Python3
  URL:=https://rpyc.readthedocs.io/
  DEPENDS:=+python3-light +supercollider
endef

define Package/python3-sc3/description
  Python3 interface for SuperCollider.
endef


$(eval $(call Py3Package,python3-sc3))
$(eval $(call BuildPackage,python3-sc3))
$(eval $(call BuildPackage,python3-sc3-src))