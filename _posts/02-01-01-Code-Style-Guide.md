---
title: Стил на писане на код
---

# Ръководсвто за стил на писане на код

Общонстта на PHP е голяма и разнообразна, съставена от неизброимо много библиотеки, рамки (frameworks) и компоненти.
Често срещано е PHP разработчик да избере няколко от тези и да ги обедини в един проект. За това  e важно PHP кода
да се придържа (възможно най-много) до общ стил на писане за да е слено за разработчиците да смесват код от различни
библиотеки за техните проекти.

[Framework Interop Group][fig] (преди това известна като 'PHP Standards Group') предложи и удобри серия от препоръки 
за стил, известни като [PSR-0][psr0], [PSR-1][psr1] и [PSR-2][psr2]. Нека интересните имена не ви заблуждават, това са
препоръки съдържащи набор от правила за писане на код, които заповат да използват от някои проекти като Drupal, Zend,
CakePHP, phpBB, AWS SDK, FuelPHP, Lithium и др. Можете да го използвате за вашите собствни проекти или да продължите да
ползвате свой собствен стил.

В най-добрия случай трябва да пишете PHP код, който отговаря на един или повече от тези стандарти, така че другите
разработчици лесно да могат да четат и работят с вашия код. Веки един от тези стандарти надгражда предходния,
т.е. PSR-1 изисква PSR-0, но не изисква PSR-2.

* [Прочети относно PSR-0][psr0]
* [Прочети относно PSR-1][psr1]
* [Прочети относно PSR-2][psr2]

Можете да ползвате [phpcs-psr][phpcs-psr] за [PHP_CodeSniffer][phpcs] за да проверявате код за съответствие със стандартите.
Използвайте [PHP Coding Standards Fixer][phpcsfixer] на Fabien Potencier за автоматично редактиране на вашия код за да отговаря
на стандартите, решавайки проблема със оправянето на всяко разминаване от стандарта самостоятелно.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[phpcs-psr]: https://github.com/klaussilveira/phpcs-psr
[phpcsfixer]: http://cs.sensiolabs.org/
