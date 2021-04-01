
#
# This is free software, licensed under the GNU General Public License v3+.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=dirk_test_programs
PKG_VERSION:=1
PKG_RELEASE:=1

PKG_LICENSE:=
PKG_LICENSE_FILES:=

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk


define Package/dirk_test_programs
  SECTION:=dirk
  CATEGORY:=Dirk
  TITLE:=simple test programs
  URL:=
  DEPENDS:=+libstdcpp $(INTL_DEPENDS)
endef

define Package/dirk/test_programs/description
  some simple test programs in C++ ...
endef

PROG_1:=cpp_intl.cpp
FILES_LIST:=$(PROG_1)

TARGET_CPPFLAGS +=-Wall -Werror -Wpedantic
TARGET_LDFLAGS += -lintl

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./files/$(FILES_LIST) $(PKG_BUILD_DIR)/
endef

define Build/Configure
endef

define Build/Compile
	$(TARGET_CXX) $(TARGET_CPPFLAGS) $(TARGET_CXXFLAGS) $(TARGET_LDFLAGS) -o $(PKG_BUILD_DIR)/$(PKG_NAME)-cpp $(PKG_BUILD_DIR)/$(PROG_1)
endef


define Package/dirk_test_programs/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME)-cpp $(1)/usr/bin/
endef

$(eval $(call BuildPackage,dirk_test_programs))

