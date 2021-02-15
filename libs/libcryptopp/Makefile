#
# Copyright (C) 2009-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libcryptopp
PKG_VERSION:=8.3.0
PKG_RELEASE:=1

PKG_SOURCE:=cryptopp$(subst .,,$(PKG_VERSION)).zip
PKG_SOURCE_URL:=http://www.cryptopp.com/
PKG_MD5SUM:=e58bd199cec1c48f62ad6eac5c024b6c
#PKG_MIRROR_HASH:=db38a15a6b1c337c665e2ebeb731dd0754b05e45504897d0f2fe4ae9f5ee589a

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

UNZIP_CMD:=unzip -q -d $(PKG_BUILD_DIR) $(DL_DIR)/$(PKG_SOURCE)

define Package/libcryptopp
        SECTION:=libs
        CATEGORY:=Libraries
        TITLE:=Crypto++ is library for creating C++ programs which use cryptographic algorithms
        URL:=https://packages.debian.org/sid/libcrypto++-dev
        DEPENDS:=+libpthread +libstdcpp
endef

define Package/package/libcryptopp
  Crypto++ is library for creating C++ programs which use cryptographic algorithms.
The library uses a Pipes & Filters architecture with heavy use of templates and abstract base classes.
endef

define Build/Prepare
        $(Build/Prepare/Default)
        cd $(PKG_BUILD_DIR) && rm -f GNUmakefile GNUmakefile-cross
endef

define Build/InstallDev
        $(INSTALL_DIR) $(1)/usr/include/cryptopp
        $(CP) $(PKG_INSTALL_DIR)/usr/include/cryptopp/* $(1)/usr/include/cryptopp/
        $(INSTALL_DIR) $(1)/usr/lib
        $(CP) $(PKG_INSTALL_DIR)/usr/lib/libcryptopp.{a,so*} $(1)/usr/lib/
endef

define Package/libcryptopp/install
        $(INSTALL_DIR) $(1)/usr/lib
        $(CP) $(PKG_INSTALL_DIR)/usr/lib/libcryptopp.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libcryptopp))
