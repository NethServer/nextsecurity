#
# Copyright (C) 2022 Nethesis S.r.l.
# SPDX-License-Identifier: GPL-2.0-only
#

include $(TOPDIR)/rules.mk
 
PKG_NAME:=ns-plug
PKG_VERSION:=0.0.1
PKG_RELEASE:=$(AUTORELEASE)
 
PKG_BUILD_DIR:=$(BUILD_DIR)/ns-plug-$(PKG_VERSION)

PKG_MAINTAINER:=Giacomo Sanchietti <giacomo.sanchietti@nethesis.it>
PKG_LICENSE:=GPL-3.0-only

include $(INCLUDE_DIR)/package.mk
 
define Package/ns-plug
	SECTION:=base
	CATEGORY:=NextSecurity
	TITLE:=NextSecurity controller client
	URL:=https://github.com/NethServer/nextsecurity-controller/
	DEPENDS:=+openvpn
	PKGARCH:=all
endef
 
define Package/ns-plug/description
	Register and connect the firewall to a NextSecurity controller instance
endef

define Package/ns-plug/conffiles
	/etc/config/ns-plug
endef

# this is required, otherwise compile will fail
define Build/Compile
endef

define Package/ns-plug/install
	$(INSTALL_DIR) $(1)/usr/share/ns-plug
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) ./files/ns-plug.init $(1)/etc/init.d/ns-plug
	$(INSTALL_BIN) ./files/ns-plug $(1)/usr/sbin/ns-plug
	$(INSTALL_CONF) ./files/config $(1)/etc/config/ns-plug
endef
 
$(eval $(call BuildPackage,ns-plug))
