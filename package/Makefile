include $(TOPDIR)/rules.mk

PKG_NAME:=rrm-nr-distributor
PKG_RELEASE:=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/rrm-nr-distributor
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Wireless
  TITLE:=802.11k Neighbor Report distributor daemon
  EXTRA_DEPENDS:=umdns
  PKGARCH:=all
endef

define Package/rrm-nr-distributor/description
    Multi-network support (different SSID for different networks)
    STA dependent band steering by advertising the other BSSes of the same AP
    Works out of the box after umdns is working
    Not too much but enough logs
endef

define Build/Prepare
        mkdir -p $(PKG_BUILD_DIR)
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/rrm-nr-distributor/install
        $(CP) ../files/* $(1)/
endef

$(eval $(call BuildPackage,rrm-nr-distributor))