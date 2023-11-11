include $(TOPDIR)/rules.mk

PKG_NAME:=autocore
PKG_FLAGS:=nonshared
PKG_RELEASE:=42

PKG_CONFIG_DEPENDS:= \
	CONFIG_TARGET_x86_64

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/target.mk

define Package/autocore
  TITLE:=auto core load balance script.
  DEPENDS:=+TARGET_x86_64:ethtool lm-sensors
endef

define Build/Compile
endef

define Package/autocore/install
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/60-autocore-reload-rpcd $(1)/etc/uci-defaults/

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/autocore $(1)/etc/init.d/

	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) ./files/cpuinfo $(1)/sbin/

	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d
	$(CP) ./files/luci-mod-status-autocore.json $(1)/usr/share/rpcd/acl.d/
endef

$(eval $(call BuildPackage,autocore))
