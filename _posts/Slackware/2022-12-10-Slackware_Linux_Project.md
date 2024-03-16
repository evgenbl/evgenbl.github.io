---
layout: post
title:  Slackware Linux Project
category: Slackware
---

**Проект Slackware Linux: справка по настройке![](/image/project/Aspose.Words.c2a4e8f6-d8c0-404d-85b5-30a5bd0e1b70.001.png)**


![](/image/project/Aspose.Words.c2a4e8f6-d8c0-404d-85b5-30a5bd0e1b70.002.png)[` `**slackware.com**/config/packages.php](http://www.slackware.com/config/packages.php)

![](/image/project/Aspose.Words.c2a4e8f6-d8c0-404d-85b5-30a5bd0e1b70.005.png)

Система упаковки Slackware использует обычные сжатые файлы tar. Система позволяет отслеживать устанавливаемые пакеты, что упрощает их обновление или удаление в будущем.

 Slackware предоставляет интерактивную программу для управления вашими пакетами. Вы можете 
 использовать **pkgtool** для обработки добавления и удаления пакетов из вашей системы.

![](/image/project/Aspose.Words.c2a4e8f6-d8c0-404d-85b5-30a5bd0e1b70.007.png)

Вы также можете использовать эти утилиты командной строки для работы с пакетами. Ниже приведен краткий обзор команд, однако перед их использованием всегда следует ознакомиться с справочными страницами.
![](/image/project/Aspose.Words.c2a4e8f6-d8c0-404d-85b5-30a5bd0e1b70.013.png)

**installpkg**

Набрав **installpkg [packagename].tgz** вы можете устанавливать пакеты в своей системе. Также есть несколько параметров командной строки:

**-warn** -Генерирует отчет о том, что произойдет, если вы
установите пакет, и отправляет отчет в standard out.

**-m**  -Преобразуйте содержимое текущего каталога и
подкаталогов в пакет с указанным вами именем. 

**-r**  -Установите содержимое текущего каталога и
подкаталогов в виде пакета с указанным вами
именем.

**removepkg**

В простейшей форме removepkg удалит указанное вами имя пакета. Общий синтаксис **removepkg packagename** . Существует несколько параметров командной строки, которые вы можете указать:

**-warn**  -Генерирует отчет о том, что произойдет, если вы
удалите пакет, и отправляет отчет в standard out. Он не удаляет пакет.

**-preserve**  -Этот параметр реконструирует поддерево пакета в: 

- /tmp/preserved\_packages/packagename , 
где **packagename** - это указанное вами имя.

**-copy**  -Создайте копию пакета в /tmp/preserved\_packages/packagename, но не удаляйте его (тот 
же эффект, что и -warn -preserve ).

**-keep**  -Сохраните временные файлы, созданные
*removepkg*. Полезно для целей отладки.

**upgradepkg**

 Обновляет установленный в данный момент пакет с указанным пакетом. Если пакеты имеют одинаковые 
  имена, вам нужно только запустить **Имя пакета upgradepkg** для выполнения обновления. Если 
  новый пакет имеет имя, отличное от текущего установленного пакета, необходимо использовать 
 этот синтаксис:

**upgradepkg oldpackagename%newpackagename**

Не добавляйте никаких дополнительных пробелов между парами старых / новых имен пакетов.

**makepkg**

 Создает новый пакет, совместимый с *Slackware*. Программа использует содержимое текущего каталога 
  для создания пакета. Обязательно ознакомьтесь с *manpag* для *makepkg* для получения информации о 
 встроенных сценариях, которые вы можете поместить в пакет *Slackware*.

**explodepkg**

 Извлекает содержимое пакета, совместимого с *Slackware*, в текущий каталог. Он не выполняет 
  встроенные скрипты в пакете. Эта утилита наиболее полезна для целей обслуживания (разнесение 
 пакета, его обновление, затем перестройка с помощью *makepkg*).
![](/image/project/Aspose.Words.c2a4e8f6-d8c0-404d-85b5-30a5bd0e1b70.013.png)

Slackware ™ - это [**торговая марка**](http://slackware.com/trademark/trademark.php) Патрика Фолькердинга.
