---
title: Настройка за Windows
isChild: true
---

## Настройка за Windows

Можете да инсталирате PHP за Windows по няколко начина. Можете да [изтеглите бинарните (компилираните) файлове](php-downloads) и до скоро можехте да ползвате '.msi'
инсталационна програма. Инсталационната програма вече не се поддържа и е спряна от PHP 5.3.0.

За обучение, експерименти и локална разработка може да ползвате вграденият уеб сървър с PHP 5.4, като няма да се тревожите за конфигурирането му.
Ако желаете "всичко в едно" решение, което включва пълен уеб сървър и MySQL, тогава инструментите [Web Platform Installer][wpi], [Zend Server CE][zsce],
[XAMPP][xampp] и [WAMP][wamp] ще ви помогнат с бързото установяване на среда за разработка под Windows. Към това трябва да добавим, че тези инструменти се различават от от тези на реалните сървъри, така че трябва да внимавате с различията в средата, ако работите под Windows, но внедрявате на Linux.

Ако реалната ви система трябва да работи на Windows, тогава IIS7 ще ви предостави най-добра производителност и стабилност.
Можете да ползвате [phpmanager][phpmanager] (графичнa приставка IIS7) за проста настройка и управление на PHP simple. IIS7 идва с вграден и готов за ползване FastCGI, само трябва да се настрои PHP като манипулатор (handler). Поддръжка и допълнтелни ресури можете да намерите на [iis.net][php-iis].

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/en/products/server-ce/
[xampp]: http://www.apachefriends.org/en/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
