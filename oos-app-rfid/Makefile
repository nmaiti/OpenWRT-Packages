#
# Copyright (C) 2018 Onion Corporation
# 
# Author: Lazar Demin  <lazar@onion.io>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
PKG_NAME:=oos-app-nfc-rfid-expansion
PKG_VERSION:=1.0.1
PKG_RELEASE:=1


PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=HEAD # dev for dev branch, HEAD for master
PKG_SOURCE_URL:=https://github.com/OnionIoT/OOS-App-RFID.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_RELEASE).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=onion
	CATEGORY:=Onion
	SUBMENU:=OS
	TITLE:=NFC-RFID Expansion : Real-time scanning of RFID tags
	DEPENDS:=+nfc-exp
endef


define Package/$(PKG_NAME)/description
NFC-RFID Expansion : Real-time scanning of RFID tags
endef

define Package/$(PKG_NAME)/install
	# install the scripts
	$(INSTALL_DIR) $(1)/usr/bin $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/omega/rfid-scan.sh $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/omega/etc/init.d/rfid-scan $(1)/etc/init.d/
	# copy the web site files
	$(INSTALL_DIR) $(1)/www/apps/oos-app-nfc-rfid-expansion
	$(CP) -r $(PKG_BUILD_DIR)/omega/www/* $(1)/www/apps/oos-app-nfc-rfid-expansion/
endef


# calls to build each package
$(eval $(call BuildPackage,oos-app-nfc-rfid-expansion))
