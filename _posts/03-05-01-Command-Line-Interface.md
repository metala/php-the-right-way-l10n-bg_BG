---
title:   Команден ред
isChild: true
---

## Команден ред

PHP  е създаден основно да се пишат уеб приложения, но освен това той е удобен за писане на програми в команден ред (CLI). Програмите за команден ред на PHP могат да ви помогнат да автоматизирате чести задачи, като тестване, внедряване и управление на приложение.

CLI PHP програмите са мощни защото можеш да изпозлваш кода на приложението си без да създаваш сигурен уеб интерфейс за него. Просто не трябва да слагате CLI PHP скриптовете в публична уеб директория!

Пробвайте да пуснете PHP от командния ред:

{% highlight bash %}
> php -i
{% endhighlight %}

Опцията `-i` ще отпечати/изпише конфигурацията на PHP - фунцията [`phpinfo`][phpinfo] . 

Опцията `-a` предоставя интерактивен шел, подобен на IRB на Руби или интерактивния шел на Питон. Има и други [полезни опции в командия режим][cli-options].

Нека напишем проста "Hello, $name" CLI програма. Създайте файл наименован `hello.php` със съдържание като това по-долу.

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP настройва две специални променливи въз основа аргументите предадени на скрипта, който пускате. [`$argc`][argc] е целочислена променлива, съдържаща броя на аргументите, а [`$argv`][argv] е променлива масив, която съдържа стойността на всеки аргумент. Първият аргумент (`$argv[0]`) е винаги името с което е стартиран вашия скрипт, в този случай `hello.php`.

Изразът `exit()` се използва с положителна числена стойностa за да извести командният ред, че е настъпила грешка. Най-често срещаните стойности на изход могат да бъдат намерени [тук][exit-codes]

За да стартирате скрипта по-горе, напишете в командия ред:

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [Научи относно пускането на PHP от команден ред][php-cli]
 * [Научи относно пускането от команден ред на PHP под Windows][php-cli-windows]

[phpinfo]: http://php.net/manual/en/function.phpinfo.php
[cli-options]: http://www.php.net/manual/en/features.commandline.options.php
[argc]: http://php.net/manual/en/reserved.variables.argc.php
[argv]: http://php.net/manual/en/reserved.variables.argv.php
[php-cli]: http://php.net/manual/en/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/en/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits
