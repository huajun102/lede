include $(TOPDIR)/rules.mk

PKG_NAME:=portalex
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_MAINTAINER:=军爷 <510461356@qq.com>
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/portalex
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Multiple PHP Sites with Nginx for portalex
  DEPENDS:=+nginx +php8-fpm +php8-cgi +php8-fasecgi  +php8-mod-curl +php8-mod-session +php8-pecl-redis +php8-mod-sqlite3 +php8-mod-mysqli 
  PKGARCH:=all
endef

define Package/portalex/description
  A package to deploy  PHP sites with Nginx on OpenWrt.
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/portalex/install
    # 安装 Nginx 主配置文件
    $(INSTALL_DIR) $(1)/etc/nginx
    $(INSTALL_CONF) ./files/etc/nginx/nginx.conf $(1)/etc/nginx/
    
    # 安装 Nginx 虚拟主机配置文件
    $(INSTALL_DIR) $(1)/etc/nginx/conf.d
    $(INSTALL_CONF) ./files/etc/nginx/conf.d/*.conf $(1)/etc/nginx/conf.d/
    
    # 安装站点1的文件
    $(INSTALL_DIR) $(1)/www/site1
    $(INSTALL_DATA) ./files/www/site1/* $(1)/www/site1/
    
    # 安装站点2的文件
    $(INSTALL_DIR) $(1)/www/site2
    $(INSTALL_DATA) ./files/www/site2/* $(1)/www/site2/
    
    # 如果需要安装初始化脚本（例如确保目录权限）
    # $(INSTALL_DIR) $(1)/etc/init.d
    # $(INSTALL_BIN) ./files/etc/init.d/multisite $(1)/etc/init.d/
endef

$(eval $(call BuildPackage,portalex))