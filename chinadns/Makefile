include $(TOPDIR)/rules.mk

PKG_NAME:=chinadns
PKG_VERSION:=1.3.2

PKG_LICENSE:=GPLv3
PKG_MAINTAINER:=clowwindy <clowwindy42@gmail.com>

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_USE_MIPS16:=0
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/chinadns
	SECTION:=net
	CATEGORY:=Network
	TITLE:=chinadns
	URL:=https://github.com/clowwindy/chinadns
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Package/chinadns/conffiles
/etc/config/chinadns
/etc/chinadns_chnroute.txt
endef

define Package/chinadns/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/chinadns.init $(1)/etc/init.d/chinadns
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/chnroute.txt $(1)/etc/chinadns_chnroute.txt
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) ./files/chinadns.config $(1)/etc/config/chinadns
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/chinadns $(1)/usr/bin
endef

$(eval $(call BuildPackage,chinadns))
