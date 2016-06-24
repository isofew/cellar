include $(TOPDIR)/rules.mk

PKG_NAME:=dns_proxy
PKG_VERSION:=1.0.0

PKG_MAINTAINER:=jtripper
PKG_LICENSE:=GPLv2

PKG_INSTALL:=1
PKG_INSTALL_DIR:=$(TOOLCHAIN_DIR)

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=DNS requests over SOCKS
  URL:=https://github.com/jtripper/dns-tcp-socks-proxy
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/root
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME) $(1)/root
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/*.conf $(1)/root
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
