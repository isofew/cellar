include $(TOPDIR)/rules.mk

PKG_NAME:=libsodium
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://download.libsodium.org/libsodium/releases/old
PKG_MD5SUM:=3093dabe4e038d09f0d150cef064b2f7

PKG_FIXUP:=libtool autoreconf
PKG_USE_MIPS16:=0
PKG_INSTALL:=1

PKG_MAINTAINER:=Damiano Renfer <damiano.renfer@gmail.com>
PKG_LICENSE:=ISC

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Portable NaCl-based crypto library
  URL:=https://github.com/jedisct1/libsodium
  MAINTAINER:=Damiano Renfer <damiano.renfer@gmail.com>
endef

CONFIGURE_ARGS+= \
	--disable-ssp \
	--enable-ssp=no \
	--enable-minimal=no

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/sodium
	$(CP) $(PKG_INSTALL_DIR)/usr/include/sodium.h $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/sodium/*.h $(1)/usr/include/sodium
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsodium.{a,so*} $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libsodium.pc $(1)/usr/lib/pkgconfig/
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsodium.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
