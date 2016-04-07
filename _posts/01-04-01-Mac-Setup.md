---
title: Настройка за Mac
isChild: true
---

## Настройка за Mac

OSX идва с пакет на PHP, който обикновено не е последната версия на PHP. Lion идва с PHP 5.3.6, 
Mountain Lion е с 5.3.10.

Можете да обновите PHP на OSX чрез множество Mac [пакетни мениждъри][mac-package-managers], като
[php-osx от Liip][php-osx-downloads] е препоръчителен.

Друга възможност е [да си го компилирате сами][mac-compile], в този случай трябва да сте инсталирали предварително или Xcode или
заместващите го ["Command Line Tools for Xcode"][apple-developer] от Mac Developer Center на Apple.

За пълен "всичко в едно" пакет, включващ PHP, Apache уеб сървър и MySQL базаданни, всичко това с приятено графично приложение за управление,
пробвайте [MAMP][mamp-downloads].

[mac-package-managers]: http://www.php.net/manual/en/install.macosx.packages.php
[mac-compile]: http://www.php.net/manual/en/install.macosx.compile.php
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
[apple-developer]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/index.html
[php-osx-downloads]: http://php-osx.liip.ch/

## Mac Setup {#mac_setup_title}

OSX идва с пакет на PHP, който обикновено не е последната версия на PHP. Lion идва с PHP 5.3.6, Mountain Lion е с 5.3.10.
Mavericks е с 5.4.17 и Yosemite - 5.5.9, но в повечето случаи това не е достатъчно, тъй като PHP 5.6 е вече на лице.

Има няколко начина за инсталиране на PHP под OS X.

### Инсталиране на PHP чрез Homebrew

[Homebrew] е пакетен мениджър с множество възможности за OS X, който може да ви помогне да инсталирате лесно PHP и редица други разширения.
[Homebrew PHP] е хранилище, което съдържа пакети свързани с PHP за Homebrew, също ще ви позволи да инсталирате PHP.

Към момента, може да инсталирате `php53`, `php54`, `php55` или `php56` използвайки `brew install` командата и да ги сменяте
като променяте вашата `PATH` променлива. Другия вариант е да използвате [brew-php-switcher][brew-php-switcher], което ще
смени версията автоматично вместо вас.

### Инсталиране на PHP чрез Macports

[MacPorts] проектът е open-source инициатива да предостави лесна за използване система за компилиране, инсталиране и 
надграждане на терминала, X11 или Aqua базиран open-source софтуер под OS X.

Macports поддържа предварително компилирани бинарни файлове, така не ви се налага да компилирате наново всяка зависимост
от source tarball файлове, спасява ви живота, ако нямате нито един пакет инсталиран на система ви.

Към момента, може да инсталирате `php53`, `php54`, `php55` или `php56` чрез `port install` командата:

    sudo port install php54
    sudo port install php55

И може да изпълните `select` командата, за да превключите на друга PHP версия:

    sudo port select --set php php55

### Инсталиране на PHP чрез phprew 

[phpbrew] е инструмент за инсталиране и менажиране на множество PHP версии. Това би било полезно, ако два различни проекта/приложения
изискват различна версия на PHP и вие не използвате виртуални машини.

### Инсталиране на PHP чрез Liip's binary installer

Друга известна опция е [php-osx.liip.ch] което дава възможност за инсталация на PHP (от версия 5.3 до версия 5.6) само с една команда.
Този метод не презаписва бинарните файлове на php инсталирани от Apple, но инсталира всичко в отделна директория (/usr/local/php5).

### Компилиране от Source Code

Друга възможност, която ви дава избор върху версията на PHP, която инсталирате, е да  [компилирате PHP сами][mac-compile].
В този случай задължително трябва да имате инсталиран [Xcode][xcode-gcc-substitution] или заместника му ["Command Line Tools for XCode"], 
които са достъпни в Apple's Mac Developer Center.

### All-in-One Installers

Решенията изброени по-горе главно инсталират единствено PHP и не осигуряват други приложения като Apache, Nginx или SQL сървър.
"All-in-one" решенията като [MAMP][mamp-downloads] и [XAMPP][xampp] ще инсталират останалия необходим софтуер, който в повечето
случаи се изисква от стандартните PHP приложения. Но за сметка на това улеснение, се губи голяма част от гъвкъвоста върху PHP
и неговите версии.


[Homebrew]: http://brew.sh/
[Homebrew PHP]: https://github.com/Homebrew/homebrew-php#installation
[MacPorts]: https://www.macports.org/install.php
[phpbrew]: https://github.com/phpbrew/phpbrew
[php-osx.liip.ch]: http://php-osx.liip.ch/
[mac-compile]: http://php.net/install.macosx.compile
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/
[xampp]: http://www.apachefriends.org/en/xampp.html
[brew-php-switcher]: https://github.com/philcook/brew-php-switcher
