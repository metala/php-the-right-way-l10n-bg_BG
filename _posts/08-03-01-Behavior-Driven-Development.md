---
title:   Разработване основано на поведение
isChild: true
---

## Разработване основано на поведение (Behavior Driven Development)

Има два типа разработване основано на поведение: SpecBDD и StoryBDD. SpecBDD се фокусира на техническото поведение или код, докато StoryBDD е насочено към бизнеса, чертите на поведение и взаимотношенията. PHP има рамки за двата типа РОП (BDD).

Със StoryBDD, вие пишете на човешки език истории които описват поведението на вашето приложение. Тези истории
могат да пускат реални тестове на вашето приложение. Рамката използвана в PHP приложенията за StoryBDD
е Behat, която е вдъхновена от [Cucumber](http://cukes.info/) за Руби (Ruby), преоект който реализира Gherkin DSL (Domain-specific Language)
за описване на чертите на поведение.

Със SpecBDD, вие пиешете спецификация как въщност вашият код трябва да се държи. Вместо да тествате функция или метод,
вие описвате как трябва да се държи. За тази работа PHP предлага рамката PHPSpec. Тази рамка е вдъхновена
от проекта [RSpec project](http://rspec.info/) за Руби.

### Инструменти за РОП (BDD)

* [Behat](http://behat.org/), the StoryBDD framework for PHP, inspired by Ruby's [Cucumber](http://cukes.info/) project;
* [PHPSpec](http://www.phpspec.net/), the SpecBDD framework for PHP, inspired by Ruby's [RSpec](http://rspec.info/) project;
* [Codeception](http://www.codeception.com) is a full-stack testing framework that uses BDD principles.
