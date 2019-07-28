---
layout: post
title: Wordpress 安装及常见错误
category: DV
description: 难点汇总
---

## Wordpress 安装
跟随[教程](https://linuxconfig.org/how-to-install-wordpress-on-debian-9-stretch-linux)



## 安装wordpress 后需要fpt 连接或安装不成功
在 wp-config.php 里添加：

```
define( 'FS_METHOD', 'direct' );

sudo chown -R www-data:www-data /var/www
```


## 安装wordpress multisite

+ 确定wordpress 文件夹在/var/www/html/ 下
+ 跟随教程 ["Create a Network"](https://codex.wordpress.org/Create_A_Network)
+ 更改 /etc/apache2/apache.conf 文件里的

```
<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>

sudo /etc/init.d/apache2 restart
```

把AllowOverride 值改为 'All'

+ 如果不成功，就删库再来一次。


## 无法登入(cookie or potential sessions issue)
在 wp-config.php 里添加：

```
define('ADMIN\_COOKIE\_PATH', '/'); 
define('COOKIE_DOMAIN', ''); 
define('COOKIEPATH', ''); 
define('SITECOOKIEPATH', '');
```

## wordpress 安装child theme
$ parent-style = mother theme name  

+ 首先进入 wp-content/theme 文件夹
+ 创建 '$parent-style + "-child"' 文件夹
+ 添加文件style.css

```
/*
 Theme Name:   Twenty Fifteen Child
 Theme URI:    http://example.com/twenty-fifteen-child/
 Description:  Twenty Fifteen Child Theme
 Author:       John Doe
 Author URI:   http://example.com
 Template:     parent-style         /* (这里改值) */
 Version:      1.0.0
 License:      GNU General Public License v2 or later
 License URI:  http://www.gnu.org/licenses/gpl-2.0.html
 Tags:         light, dark, two-columns, right-sidebar, responsive-layout, accessibility-ready
 Text Domain:  twenty-fifteen-child
*/
```
并且把 'Template' 的值改为 $parent-style

+ 添加文件 functions.php

```
<?php
function my\_theme\_enqueue_styles() {

    $parent_style = 'parent-style'; // 这里改值

    wp\_enqueue\_style( $parent\_style, get\_template\_directory\_uri() . '/style.css' );
    wp\_enqueue\_style( 'child-style',
        get\_stylesheet\_directory_uri() . '/style.css',
        array( $parent_style ),
        wp\_get\_theme()->get('Version')
    );
}
add\_action( 'wp\_enqueue\_scripts', 'my\_theme\_enqueue\_styles' );
?>
```
+ ok重新登陆

## wordpress update password
1. encryt your Password to Hash through MD5 et cetera.
2. login to your server
3. login to mysql      // %mysql -r root -p
4. // %show databases;
5. use the WP database; // % use "xxx";
6. // %show tables;
7. // %select id, user_login, user_pass from "the table that you have";
8. // %update "the table that you have" set user_pass="your hash" where id = "your user id";
9. repeat 7 to confirm.
