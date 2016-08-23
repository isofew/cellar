include $(TOPDIR)/rules.mk

PKG_NAME:=ipxor
PKG_VERSION:=1.0.1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/isofew/ipxor/archive
PKG_MD5SUM:=76eb7dee64a406c4e84571b90d0294fb

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=ipv4/v6 xor mask
	URL:=https://github.com/isofew/ipxor
	DEPENDS:=+libstdcpp +libnetfilter-queue
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME) $(1)/bin/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
