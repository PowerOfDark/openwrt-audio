include $(TOPDIR)/rules.mk

PKG_NAME:=python3-dbus
PKG_VERSION:=1.2.16
PKG_RELEASE:=5

PYPI_NAME:=dbus-python
PKG_HASH:=11238f1d86c995d8aed2e22f04a1e3779f0d70e587caffeab4857f3c662ed5a4

PKG_MAINTAINER:=Oskari Rauta <oskari.rauta@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_FIXUP:=patch-libtool

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/python3-dbus
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python bindings for libdbus
  DEPENDS:=$(INTL_DEPENDS) +libdbus +glib2 +python3-light
endef

define Package/python3-dbus/description
  dbus-python is the original Python binding for dbus,
  the reference implementation of the D-Bus protocol.
endef

PYTHON3_PKG_SETUP_ARGS:=

CONFIGURE_VARS += \
	PYTHON_LIBS="-L$(PYTHON3_LIB_DIR) -L$(STAGING_DIR)/usr/lib -lpython$(PYTHON3_VERSION)" \
	PYTHON_INCLUDES="-I$(PYTHON3_INC_DIR)" \
	PYTHON_VERSION="$(PYTHON3_VERSION)"

CONFIGURE_ARGS += \
	--disable-installed-tests

define Py3Build/Compile
	$(call Py3Build/Compile/Default)
	$(MAKE_VARS) $(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR) $(MAKE_FLAGS) \
		DESTDIR="$(PKG_INSTALL_DIR)" install
	#$(RM) $(PKG_INSTALL_DIR)/usr/lib/python$(PYTHON3_VERSION)/site-packages/*.la
endef

$(eval $(call Py3Package,python3-dbus))
$(eval $(call BuildPackage,python3-dbus))
$(eval $(call BuildPackage,python3-dbus-src))
