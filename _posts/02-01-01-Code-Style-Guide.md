---
title: Стил на писане на код
---

# Ръководство за стил на писане на код

PHP обществото е голямо и разнообразно, създало е неизброимо много библиотеки, рамки (frameworks) и компоненти. Често срещано е PHP разработчик да избере няколко от стандарта и да ги обедини в един проект. Затова e важно PHP кода да се придържа (възможно най-много) до общ стил на писане, за да е лесно за разработчиците да смесват код от различни библиотеки за техните проекти.

[Framework Interop Group][fig] (преди това известна като "PHP Standards Group") предложи и одобри серия от препоръки за стил, известни като [PSR-0][psr0], [PSR-1][psr1] и [PSR-2][psr2]. Нека интересните имена не ви заблуждават, това са препоръки съдържащи набор от правила за писане на код, които започват да се използват от някои проекти, като Drupal, Zend, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium и др. Можете да ги използвате за вашите собствени проекти или да продължите да ползвате свой собствен стил.

В най-добрия случай, пишейки код трябва да се придържате към определен стандарт. Това може да бъде всяка комбинация от PSR, или някой от стандартите създадени от PEAR или Zend.Това ще направи приложенията ви по-консистентни и ще позволи на други разработчици да четат кода ви и да работят с него.

* [Прочети относно PSR-0][psr0]
* [Прочети относно PSR-1][psr1]
* [Прочети относно PSR-2][psr2]
* [Прочети относно стандартите на PEAR][pear-standarts]
* [Прочети относно стандартите на Zend][zend-standarts]

Можете да ползвате [PHP_CodeSniffer][phpcs], за да проверявате код за съответствие със стандартите, както и приставки към редактори, като [Sublime Text 2][sublime-phpcs], за резултати в реално време.

Използвайте [PHP Coding Standards Fixer][phpcsfixer] на Fabien Potencier който редактира вашия код, така че да отговаря на стандартите и решава проблема с оправянето на всяко разминаване от стандарта самостоятелно.

Английския език е препоръчителен за всички имена на символи и структури. Коментарите могат да се пишат на всеки език, стига да са лесни за четене от всички настоящи и бъдещи потребители, които биха работили с кода.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[pear-standarts]: http://pear.php.net/manual/en/standards.php
[zend-standarts]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[sublime-phpcs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
