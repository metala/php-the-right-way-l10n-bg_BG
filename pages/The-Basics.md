---
layout: page
title: Основите
---

# Основите

## Оператори за сравнение

Операторите за сравнение са често непрочетени и пропускани, в следствие на което водят до неочаквани изходи. Един пример
се крие в стриктните сравнения (сравняването на булева стойност с цяло число).

{% highlight php %}
<?php
$a = 5;   // 5 като цяло число

var_dump($a == 5);       // сравнява по стойсност; върша истина (true)
var_dump($a == '5');     // сравнява по стойност (пропуска типа); връща истина (true)
var_dump($a === 5);      // compare type/value (integer vs. integer); връша истина (true)
var_dump($a === '5');    // compare type/value (integer vs. string); връща лъжа (false)

/**
 * Стриктни сравнения
 */
if (strpos('testing', 'test')) {    // 'test' се намира на позиция 0, което се интерпретира като булева лъжа 'false'
    // още код...
}

// А не

if (strpos('testing', 'test') !== false) {    // истина (true), в следствие на стриктното сравнение (0 !== false)
    // още код...
}
{% endhighlight %}

* [Оператори за сравнение](http://php.net/manual/bg/language.operators.comparison.php)
* [Таблици за сравнение на типове в PHP](http://php.net/manual/bg/types.comparisons.php)

## Условни аргументи

### Конструкцията if

Като се ползват конструкциите 'if и else' в фунцкия или клас, съществува забуда,
че 'else' трябва да бъде ползван за да укаже потенциален изход. Но когато случаят е,
че трябва да върне стойност, 'else' не е нужен, той като 'return' ще прекрати
функцията и 'else' ще бъде пропуснат.

{% highlight php %}
<?php
function test($a)
{
    if ($a) {
        return true;
    }
    return false;    // else не е нужен
}

// А не

function test($a)
{
    if ($a) {
        return true;
    } else {
        return false;
    }
}
{% endhighlight %}

* [Конструкцията If](http://php.net/manual/bg/control-structures.if.php)

### Конструкцията switch

Конструкцията switch е великолепен начин за избягване на писане на безкрайни if/elseif/else, но трябва да се запознаете
с някои неща относно конструкцията switch:

- Конструкциата switch сравнява единствено по стойност, а не по тип (еквивалентно '==')
- Те обхождат всеки един case последователно докато не достигне съвпадение. Ако не намери съвпадение, тогава отива на default (ако е описан)
- Без 'break', ще продължат изпълнението надолу по кода докато не достигнат break/return или край на switch.
- Когато се намира в функция 'return' преждевременно прекратява switch-а и връша стойността от функцията, което премахва нуждата от последвал break

{% highlight php %}
<?php
$answer = test(2);    // кодът от от 'case 2' и 'case 3' ще бде изпълнен

function test($a)
{
    switch ($a) {
        case 1:
            // код...
            break;             // използва се за break за прекратяване на конструкцията switch
        case 2:
            // код...          // без break, изпълнението ще продължи изпълнението до break или return, т.е. 'case 3'
        case 3:
            // код...
            return $result;    // в фунцкия, 'return' ще прекрати функцията
        default:
            // код...
            return $error;
    }
}
{% endhighlight %}

* [Конструкцията switch](http://php.net/manual/bg/control-structures.switch.php)
* [PHP switch (английски)](http://phpswitch.com/)

## Голбално пространство от имена

Когато се ползват постранства от имена, може да намерите вашият код да се изпълнява в грешен обхват (scope) за вътрешни
методи. За да оправите това дефинирайте метода глобално, като добавите обратна наклонена черта пред името на метода.

{% highlight php %}
<?php
namespace phptherightway;

function fopen()
{
    $file = \fopen();    // нашата функция е със същото име като вътрешна функция
                         // изпълняваме глобалната като добавим '\' пред името.
}

function array()
{
    $iterator = new \ArrayIterator();    // ArrayIterator е вътрешен клас. Използвайки го без '\'
                                         // ще се изпълни в локалното пространство от имена
}
{% endhighlight %}

* [Глобално пространство](http://php.net/manual/bg/language.namespaces.global.php)
* [Global rules (английски)](http://php.net/manual/en/userlandnaming.rules.php)

## Низове

### Конкатенация

- Ако линията надминава препоръчителната дължина (120 символа), опитайте се да го разделите на части и да ги конкатенирате
- За четимост е най-добре да ползвате оператора за конкатенация '.', а не този за конкатенация и присвояване '.='
- Когато сте в обхвата, където е декларирана променливата, отместете когато конкатенацията съдържа "нов ред"


{% highlight php %}
<?php
$a = 'Пример на няколко реда,'      // оператор за конкатенация (.)
    . "\n"                          // отместване при "нов ред"
    . 'за това какво трябва да правим';

// А не

$a  = 'Същият пример на няколко реда,';    // оператор за конкатенация и присвояване (.=)
$a .= "\n";
$a .= 'но за това какво да НЕ правим';
{% endhighlight %}

* [Оператори за низове](http://php.net/manual/bg/language.operators.string.php)

### Низови типове

Надяваме се с тази секция да обясним разликите между типовете 
низове и техните предимства и начини за ползване.

#### Апострофи

Поставяне в апострофи е най-простият начин за дефиниране на низ и често най-бързият. Скоростта се крие в това,
че PHP интерпретатора не прави разбор на низа (за променливи). Този тип е най-добър за:

- Низове, който не трябва да им се прави разбор
- Изпизването на променлива в чист текст

{% highlight php %}
<?php
echo 'This is my string, look at how pretty it is.';    // няма нужда от разбор на прост низ

/**
 * Изход:
 *
 * This is my string, look at how pretty it is.
 */
{% endhighlight %}

* [Поставяне в апострофи](http://www.php.net/manual/bg/language.types.string.php#language.types.string.syntax.single)

#### Кавички

Поставянето в кавички представлява швецарско ножче за работа с низове, но е по-бавни защото трябва да им се прави разпознаване.
Най-добре служат за:

- Екранирани низове
- Низове с множество променливи и чист текст
- Сбиване на многоредова конкатенация и подобравяне на четимостта

{% highlight php %}
<?php
echo 'phptherightway is ' . $adjective . '.'     // пример с единични кавички би използвал множество конкатенации
    . "\n"                                       // за променливите и екранирания низ
    . 'I love learning' . $code . '!';

// А не

echo "phptherightway is $adjective.\n I love learning $code!"  // Вместо конкатенираме, двойните кавички
                                                               // ни позволяват да ползваме низ за разпознаване
{% endhighlight %}

Когато се ползват двойни кавички, които съдържат променливи, често се случва променливата да се допира до
друг символ. Тогава PHP няма да разпознае променливата, защото е скрита. За да оправим този проблем,
Ограждаме променливаа в къдрави скоби.

{% highlight php %}
<?php
$juice = 'plum';
echo "I drank some juice made of $juices";    // променливата $juice няма да бъде разпозната

vs.

$juice = 'plum';
echo "I drank some juice made of {$juice}s";    // променливата $juice ще бъде разпозната

/**
 * Сложни променливи също ще бъдат разпознати, коато са в къдрави скоби
 */

$juice = array('apple', 'orange', 'plum');
echo "I drank some juice made of {$juice[1]}s";   // $juice[1] ще бъде разпозната
{% endhighlight %}

* [Кавички](http://www.php.net/manual/bg/language.types.string.php#language.types.string.syntax.double)

#### Nowdoc синтаксис

Синтаксисът Nowdoc се появява за първи път в 5.3 и вътрешно действа като единични кавички, за разлика от това че е пригоден
за ползване при многоредови низове без нуждата от конкатенация.

{% highlight php %}
<?php
$str = <<<'EOD'             // установява се с <<<
Example of string
spanning multiple lines
using nowdoc syntax.
$a does not parse.
EOD;                        // затварящият 'EOD' трябва да е в началото на нов ред

/**
 * Изход:
 *
 * Example of string
 * spanning multiple lines
 * using nowdoc syntax.
 * $a does not parse.
 */
{% endhighlight %}

* [Синтаксис тип Nowdoc](http://www.php.net/manual/bg/language.types.string.php#language.types.string.syntax.nowdoc)

#### Heredoc синтаксис

Синтаксисът Heredoc вътрешно работи като двойни кавички и е пригоден за работа с многоредови
низове, без нужда от конкатенация.

{% highlight php %}
<?php
$a = 'Variables';

$str = <<<EOD               // Установява се чрез <<<
Example of string
spanning multiple lines
using heredoc syntax.
$a are parsed.
EOD;                        // затварящият 'EOD' трябва да е в началото на нов ред

/**
 * Изход:
 *
 * Example of string
 * spanning multiple lines
 * using heredoc syntax.
 * Variables are parsed.
 */
{% endhighlight %}

* [Синтаксис тип Heredoc](http://www.php.net/manual/bg/language.types.string.php#language.types.string.syntax.heredoc)

## Условен оператор

Условените оператори са страхотен начин за сбиване на код, но често се прекалява с използването им.
Вътреки, че те могат да се вместят един в друг, препоръчва се да се използва само по един на линия
с цел четимост.

{% highlight php %}
<?php
$a = 5;
echo ($a == 5) ? 'yay' : 'nay'; // Един на линия

А не:

// вложени условни оператори
$b = 10;
echo ($a) ? ($a == 5) ? 'yay' : 'nay' : ($b == 10) ? 'excessive' : ':(';    // търде много влагане, жертва се четимостта
{% endhighlight %}

Тройните оператори, също имат ограниения и не могат да бъдат ползвани за връшане ('return') на стойност.

{% highlight php %}
<?php
$a = 5;
echo ($a == 5) ? return true : return false;    // този пример ще хвърли грешка,
{% endhighlight %}

* [Условен/троен оператор](http://php.net/manual/bg/language.operators.comparison.php)

## Деклариране на променливи

Понякога, програмистите опитват да пишат "по-чист" код, като предефинират променливи с друго име. Реално това
удвоява заетата памет от конкретния скрипт. За примера по-долу, нека кажем че примерният низ съдържа данни
заемащи 1МБ памет. При копирането им в променлива, се увеличава използваната памет до 2МБ.

{% highlight php %}
<?php
$about = 'A very long string of text';    // използва 2MB памет
echo $about;

vs.

echo 'A very long string of text';        // Използва 1MB памет
{% endhighlight %}

* [Съвети за подобрение на производителнсотта (английски)](https://developers.google.com/speed/articles/optimizing-php)
