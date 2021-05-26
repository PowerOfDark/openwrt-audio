include $(TOPDIR)/rules.mk

PKG_NAME:=python3-yamlable
PKG_VERSION:=1.0.3
PKG_RELEASE:=1

PKG_HASH:=0ef68de44e7ca8ac0bf7de0fb497ca4687ebc9798af05ef42e5e07facf0f9137
PYPI_NAME:=yamlable
PKG_MAINTAINER:=Przemysław Rozwałka
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_FIXUP:=patch-libtool

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk


define Package/python3-yamlable
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Wrapper of PyYaml
  URL:=https://github.com/smarie/python-yamlable
  DEPENDS:=+python3-light +python3-yaml
endef

define Package/python3-yamlable/description
  A thin wrapper of PyYaml to convert Python objects to YAML and back
endef


$(eval $(call Py3Package,python3-yamlable))
$(eval $(call BuildPackage,python3-yamlable))
$(eval $(call BuildPackage,python3-yamlable-src))