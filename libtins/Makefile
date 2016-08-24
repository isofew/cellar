include $(TOPDIR)/rules.mk

PKG_NAME:=libtins
PKG_VERSION:=3.4
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/mfontanini/libtins/archive
PKG_MD5SUM:=55fa97b9a19f9008a0c674f5f559e4f7

PKG_MAINTAINER:=Matias Fontanini
PKG_LICENSE:=BSD-2

PKG_INSTALL:=1
PKG_INSTALL_DIR:=$(TOOLCHAIN_DIR)

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=High-level, multiplatform C++ network packet sniffing and crafting library
  URL:=https://github.com/mfontanini/libtins
  DEPENDS:=+libpcap +libstdcpp +libopenssl
endef

define Build/Configure
	IN_OPENWRT=1 \
	AR="$(TOOLCHAIN_DIR)/bin/$(TARGET_CROSS)ar" \
	AS="$(TOOLCHAIN_DIR)/bin/$(TARGET_CC) -c $(TARGET_CFLAGS)" \
	LD="$(TOOLCHAIN_DIR)/bin/$(TARGET_CROSS)ld" \
	NM="$(TOOLCHAIN_DIR)/bin/$(TARGET_CROSS)nm" \
	CC="$(TOOLCHAIN_DIR)/bin/$(TARGET_CC)" \
	GCC="$(TOOLCHAIN_DIR)/bin/$(TARGET_CC)" \
	CXX="$(TOOLCHAIN_DIR)/bin/$(TARGET_CROSS)g++" \
	TARGET_CPPFLAGS="$(TARGET_CPPFLAGS)" \
	TARGET_CFLAGS="$(TARGET_CFLAGS)" \
	TARGET_LDFLAGS="$(TARGET_LDFLAGS)" \
	cmake $(PKG_BUILD_DIR)/CMakeLists.txt \
		-DCMAKE_INSTALL_PREFIX=/usr
		-DLIBTINS_ENABLE_CXX11=0
endef

define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR)/usr/include/tins
	$(CP) $(PKG_BUILD_DIR)/include/tins/*.h $(STAGING_DIR)/usr/include/tins/
	$(INSTALL_DIR) $(STAGING_DIR)/usr/include/tins/dot11
	$(CP) $(PKG_BUILD_DIR)/include/tins/dot11/*.h $(STAGING_DIR)/usr/include/tins/dot11/
	$(INSTALL_DIR) $(STAGING_DIR)/usr/include/tins/tcp_ip
	$(CP) $(PKG_BUILD_DIR)/include/tins/tcp_ip/*.h $(STAGING_DIR)/usr/include/tins/tcp_ip/
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) V=99
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/lib/libtins.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
