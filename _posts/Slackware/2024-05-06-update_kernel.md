---
layout: post
title: Обновление ядра в Slackware
category: Slackware
---

### Обновление ядра в Slackware 15

(Обновлял ядра в версиях 14.2 и 15)

1) /usr/share/mkinitrd/mkinitrd_command_generator.sh -k 5.4.72 | bash

2) mkinitrd -c -k 5.4.72 -m ext4 -r /dev/sdd2 -f ext4

Но они не очень удобны тем, что нужно предварительно посмотреть на версию свежеустановленного ядра, чтобы указать ее в параметрах и не опечататься, равно как и в других параметрах.

Второй способ проверен несколько раз.Работает.

Первый не пробовал.Думаю тоже рабочий.


### Делаю так:

- slackpkg update

- slackpkg update gpg

- slackpkg upgrade-all

- lilo

-  mkinitrd -c -k 5.4.72 -m ext4 -r /dev/sdd2 -f ext4 (смотрите версию своего ядра)

- lilo

P.S.

в /etc/slackpkg/blacklist - ***ничего не надо изменять что касается ядра***



