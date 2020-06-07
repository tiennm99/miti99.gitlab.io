+++ 
draft = false
date = 2020-05-01T07:00:00+07:00
title = "Theme cho GRUB"
description = ""
slug = "" 
tags = ["Arch", "Linux", "GRUB"]
categories = []
externalLink = ""
series = []
+++

Bạn muốn có giao diện GRUB đẹp hơn? Hôm nay mình sẽ chia sẻ cách để tạo giao diện GRUB đẹp hơn một tí. Ở đây mình ví dụ là theme litarvan có sẵn trong repo của Arch:
```shell
yay -S grub-theme-vimix
```
Sau đó thêm dòng sau vào file `/etc/default/grub`:
```shell
GRUB_THEME=”/usr/share/grub/themes/Vimix/theme.txt”
```
Cập nhật grub và khởi động lại tận hưởng nào! 😀
```shell
grub-mkconfig -o /boot/grub/grub.cfg
```
Nếu bạn không thích theme này thì có thể tự tải theme hoặc tự tạo theme mình thích. Lưu ý là nên để ở thư mục nào đó mà hệ thống có thể truy cập được không cần quỵền người dùng nhé. VD `/usr/share` như trên.

Chúc các bạn có được một GRUB thật đẹp nhé! Hẹn gặp lại.
