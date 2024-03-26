include $(TOPDIR)/rules.mk

PKG_NAME:=sshpiper
PKG_VERSION:=1.2.8
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/tg123/sshpiper
PKG_SOURCE_VERSION:=v$(PKG_VERSION)

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Yuchao Guo <ihidchaos@gmail.com>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/tg123/sshpiper
GO_PKG_BUILD_PKG:=github.com/tg123/sshpiper/cmd/sshpiperd

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/../feeds/packages/lang/golang/golang-package.mk

define Package/sshpiper
  SECTION:=net
  CATEGORY:=Network
  TITLE:=The missing reverse proxy for ssh scp
  URL:=https://github.com/tg123/sshpiper
  DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/sshpiper/description
  sshpiper is the reverse proxy for sshd.
endef

ifneq ($(CONFIG_USE_MUSL),)
  TARGET_CFLAGS += -D_LARGEFILE64_SOURCE
endif

define Package/sshpiper/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/sshpiperd $(1)/usr/bin
endef

$(eval $(call GoBinPackage,sshpiper))
$(eval $(call BuildPackage,sshpiper))
