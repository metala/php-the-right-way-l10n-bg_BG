---
name:    Дата и време
isChild: true
---

## Дата и време

В PHP има клас на име DateTime, който помага при четенето, писането и сравняването и изчисляването на дата и час.
Има много фунцкии за работа с дата и час в PHP, но DateTime специално предлага хубав обектно-ориентиран интерфейс за
работа с дата и час. Има възможност за работа с вчасовият пояси, но това е отвъд въведенитео.

За да започнете работата с DateTime, преобразувайте сурова дата и час в обект чрез `createFromFormat()` метод фабрика
или чрез `new \DateTime` за да вземете текущата дата и час. Изпозлвайте метода `format()` за да преобразувате DateTime обратно в низ за изход.
{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('m/d/Y') . "\n";
{% endhighlight %}

Сметките с DateTime се правят чрез класа DateInterval. Методите като `add()` и `sub()` на класа DateTime взикат DateInterval
за аргумент. Не пишере код който очаква определен брой секунди всеки ден, смятата на зимно и лятно време, катко и промяната
на часовия пояс може да доведе до грешка. Използвайте интервали от време вместо това. За да изчислите разликата между две дати,
използвайте `diff()` метода. Той ще върне нов DateInterval обект, който е много лесе нза показване.
{% highlight php %}
<?php
// create a copy of $start and add one month and 6 days
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Difference: ' . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Difference: 1 month, 6 days (total: 37 days)
{% endhighlight %}

На обекти от тип DateTime можеш да прилагаш обикновено сравненеие:
{% highlight php %}
<?php
if ($start < $end) {
    echo "Start is before end!\n";
}
{% endhighlight %}

Един последен пример ще демонстрира класа DatePeriod. Той се използва за обхождане на повтарящи се събития.
Може да приеме два DateTime обекта, т.е. начало и край и интервал интервал, и ще върне всички обекти по средата.
{% highlight php %}
<?php
// output all thursdays between $start and $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // output each date in the period
    echo $date->format('m/d/Y') . ' ';
}
{% endhighlight %}

* [Прочети относно DateTime][datetime]
* [Прочети относно форматирането][dateformat] (опциите които форматирането приема)

[datetime]: http://www.php.net/manual/book.datetime.php
[dateformat]: http://www.php.net/manual/function.date.php
