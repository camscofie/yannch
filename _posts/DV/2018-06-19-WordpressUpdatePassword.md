---
layout: post
title: wordpress update password
description: some dumb thing
category: DV
---

1. encryt your Password to Hash through MD5 et cetera.
2. login to your server
3. login to mysql      // %mysql -r root -p
4. // %show databases;
5. use the WP database; // % use "xxx";
6. // %show tables;
7. // %select id, user_login, user_pass from "the table that you have";
8. // %update "the table that you have" set user_pass="your hash" where id = "your user id";
9. repeat 7 to confirm.
10. bye
