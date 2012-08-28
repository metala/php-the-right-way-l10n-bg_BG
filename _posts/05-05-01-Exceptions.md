---
title:   Изключения
isChild: true
---

## Изключения (Exceptions)

Изключенията са стандартна част от повечето популярни програмни езици, но често са пренебрегвани от PHP програмистите.
Езици като Ruby са крайно насочени към изключенията, т.е. дори ако нещо се случи, като провалена HTTP заявка или 
заявка към БД даде грешка или дори статична картина не може да бъде намерена, Ruby (или gem-а, който се ползва) ще
хвърли изключение към екрана, и на момента разбираш, че е настъпила грешка. 

При PHP попринцип, често липсва тази възможност, и примерно проблемно извикване на `file_get_contents()` ще върне `FALSE`
и ще изведе предупреждение. Много стари рамки като CodeIgniter ще върнат `false`, и ще запишат съобщение в log-а и вероятно 
ще предоставят метод, като `$this->upload->get_error()` за да видиш каква е грешката. Проблема възниква в това, че трябва да
отидете в документацията и да проверите какъв е метода за грешка за този клас вместо да бъде максимално видима грешката.

Друг проблем когато клас направиш клас автоматично след като изведе грешката на екрана да излезе от цялата програма.
Когато се прави това вие пречите на друг разработчик, динамично да обработи грешката. Изключенията трябва да бъдат хвърляни
за да се извести разработчика че е настъпила грешка, тогава той може да реши как да я обработи, пример:

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // The validation failed
}
catch(Fuel\Email\SendingFailedException $e)
{
    // The driver could not send the email
}
{% endhighlight %}

### SPL изключения

Изключението по поддразбиране няма значение и най-практикувания начин е като им се даде име: 

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

Това означава, че вие можете да добавите множесто блокове, които да се справят с изключенията по различен начин.
Това може да доведе до _много_ видове изключения, някои от които могат да бъдат избегнати с SPL изключения 
предоставени в [разширението SPL][splext]. 

Например позлвате вълшебния метод `__call()` и невалиден метод е поискан, вместо да хвърляте обикновено изключение,
или да създавате специален тип изключение за това, можете просто да `throw new BadFunctionCallException;`.

* [Прочетете относно изключенията][exceptions]
* [Прочетете относно SPL изключенията][splexe]
* [Влагане на изключения в PHP][nesting-exceptions-in-php]
* [Най-добри практики в PHP 5.3 за изключенията][exception-best-practices53]

[exceptions]: http://php.net/manual/en/language.exceptions.php
[splexe]: http://php.net/manual/en/spl.exceptions.php
[splext]: /#standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
