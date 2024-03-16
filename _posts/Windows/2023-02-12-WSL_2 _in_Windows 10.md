---
layout: post
title:  Установите WSL 2 в Windows 10
category: Windows
---

**Требования**

***Для установки WSL 2 в Windows 10 вам понадобятся следующие вещи:***

- Windows 10 мая 2020 г. (20.04), Windows 10 мая 2019 г. (19.03) или Windows 10 ноября 2019 г. (19.09)

- Компьютер с поддержкой виртуализации Hyper-V

- Обновление Windows 10 за май 2020 года было выпущено в мае 2020 года (почувствуй себя капитаном очевидность), но не все устройства могут обновиться сразу. 

Чтобы узнать, доступно ли обновление Windows 10 May 2020 на вашем компьютере, перейдите в Настройки > Обновление и безопасность > Центр обновления Windows.

В августе Microsoft перенесла WSL 2 на старые версии Windows 10. Любой пользователь сборок 19.03 или 19.09 также может установить WSL 2, но сначала придется обновиться по вот этой ссылке Windows KB4566116.

Технически вы можете установить WSL 2 на «инсайдерскую» сборку Windows 10 build 18917 или новее. Я не слишком знаком с тем, как работает «инсайдерская» система сборки, поэтому просто имейте в виду, что остальная часть этого сообщения основана на использовании стабильной версии Windows.

Ваш компьютер также должен поддерживать виртуализацию Hyper-V для запуска WSL 2. Чтобы убедиться, вы можете проверить поддержку Hyper-V.

Для этого вам понадобиться нажмите **Win + R** и набрать в открывшемся диалоговом окошке команду **msinfo32**.

 Открывшийся список прокрутите до конца и найдите четыре пункта про **Hiper V**:

- расширения режима мониторинга виртуальной машины;

- расширения для преобразования адресов второго уровня;

- виртуализация включена во встроенном ПО;

- предотвращение выполнения данных;

Если все они имеют значение «Да», поздравляю, у вас все хорошо и ваша ось поддерживает технологию Hiper V.

*Если же ваша машинка не соответствует обоим требованиям, штош, вы не сможете установить или включить WSL 2, но вы можете использовать WSL 1*.

***Процесс установки WSL 2 в Windows 10 таков:***

- Включить WSL 2

- Включите «Платформу виртуальных машин»

- Установите WSL 2 по умолчанию

- Установите дистрибутив Linux

Я шаг за шагом пройду по каждому из этих пунктов с помощью приложения - PowerShell, которое вам нужно запустить от имени администратора. PowerShell легко найти в меню «Пуск» Windows.

Примечание: WSL 1 можно установить и с помощью графического интерфейса, но гораздо быстрее использовать командную строку, но, поскольку WSL — это инструмент командной строки, имеет смысл и устанавливать его с помощью нее!

**1.Включите WSL**

Независимо от того, какую версию WSL вы хотите использовать, вам сначала нужно включить ее. Для этого откройте инструмент PowerShell от имени администратора и выполните команду ниже. Будьте осторожны, чтобы не набрать и не пропустить какой-либо символ в команде:

        dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

Если по каким-то причинам вы хотите использовать т WSL 1 – переходите к пункту 4.

**2.Включите «Платформу виртуальных машин»**

WSL 2 требует, чтобы была включена функция «Платформа виртуальных машин» в Windows 10. Она отделена от Hyper-V и предоставляет некоторые из наиболее интересных интеграций платформ, доступных в новой версии подсистемы Windows для Linux.

Чтобы включить платформу виртуальных машин в Windows 10 (20.04), откройте PowerShell от имени администратора и выполните команду:

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
Чтобы включить платформу виртуальных машин в Windows 10 (19.03, 19.09), откройте PowerShell от имени администратора и выполните:

    Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform -NoRestart

На этом этапе вам стоит перезагрузить систему, чтобы убедиться, что все компоненты встали как надо и все работает так как задумано.

**3.Установите WSL 2 по умолчанию**

Откройте PowerShell от имени администратора и выполните эту команду, чтобы установить WSL 2 в качестве версии WSL по умолчанию:

    wsl --set-default-version 2

Вы можете (в любое время) настроить дистрибутив для работы в режиме WSL 1, если вам нужно.

**4.Установите дистрибутив**
 
С WSL и необходимой технологией виртуализации все, что вам остается сделать, это выбрать и установить дистрибутив Linux из Microsoft Store.

Доступно несколько различных дистрибутивов, включая OpenSUSE, Pengwin, Fedora Remix и Alpine Linux. Но моя личная рекомендация (естественно) - Ubuntu 20.04 LTS (хотя также доступны 18.04 LTS и 16.04 LTS).

Чтобы установить Ubuntu в Windows 10, откройте приложение Microsoft Store, найдите «Ubuntu 20.04» и нажмите кнопку «Получить»:

    Ubuntu 20.04 LTS в магазине Microsoft Store

Пока вы находитесь в Microsoft Store, я настоятельно рекомендую вам также установить приложение Windows Terminal с открытым исходным кодом. Этот инструмент разработан, чтобы предоставить вам наилучшие возможности WSL:

    Терминал Windows в Магазине Microsoft

**5.Используйте WSL 2**

Когда вы устанавливали Ubuntu (или другой дистрибутив Linux), в меню «Пуск» был добавлен ярлык. Используйте его, чтобы «открыть» Ubuntu (или любой другой дистрибутив, который вы выбрали). В первый раз, когда вы запустите дистрибутив, все будет казаться ужасно медленным. Все в порядке, это норма; дистрибутив должен распаковаться и распаковать все свое содержимое – заварите чайку, подождите, только не прерывайте процесс.

Вам также будет предложено установить имя пользователя и пароль для использования в дистрибутиве. По возможности выбирайте то, что вы не забудете.

Преобразование Ubuntu на WSL 1 в WSL 2
Если вы используете WSL 1, вы можете обновить существующую версию до WSL 2. Чтобы преобразовать существующий дистрибутив WSL 1 в WSL 2, выполните в PowerShell следующее команду:

    wsl.exe --set-version Ubuntu 2

Только замените «Ubuntu» в вышеприведённой команде названием того дистрибутива, который вы запускаете при запуске WSL 1

>Взято с:
>
> [ссылка](https://omgubuntu.ru/kak-ustanovit-wsl-2-v-windows-10/)