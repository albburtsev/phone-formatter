<img src="https://raw.githubusercontent.com/1234ru/phone-formatter/master/docs/live.gif" width="400" align="center">

Автоматическое форматирование номеров телефонов при вводе их в поля форм значительно 
облегчает визуальный контроль за правильностью набора. От пользователя при этом требуется вводить только цифры. 

Данная библиотека позволяет просто и быстро решить эту задачу, обеспечивая форматирование по шаблонам, которые составляются разработчиком по своему усмотрению.

Библиотека выполнена на чистом Javascript без зависимостей от внешних компонентов.


## Как пользоваться

1. Скопировать файл `lib.js` и подключить его.  


2. Составить список шаблонов телефонных номеров. Пример:

```javascript
var numberPatterns = [
  '+7 (NNN) NNN-NN-NN',  // Россия и Казахстан
  '+375 NN NNN-NN-NN',   // Беларусь
  '+38 (0NN) NNN-NN-NN', // Украина
  '+1 (NNN) NNN-NNNN',   // США
];
```

3. Установить слежение за нужными полями. Например, за всеми полями с типом `tel`:

```javascript
document.querySelectorAll( 'input[type=tel]' ).forEach( function( input ) {
    new Freedom.PhoneFormatter( numberPatterns ).attachToInput( input );
} );
```
(Freedom - веб-фреймворк, в рамках которого ведется разработка, отсюда и название пространства имён.)


## Особенности

* все перечисленные шаблоны будут анализироваться, и применяться будет тот, который
по начальным цифрам соответствует текущему вводу пользователя

* в пустое поле при получении им фокуса сразу подставляется начальный фрагмент первого из 
  указанных шаблонов; если пользователь в итоге ничего не ввёл, при потере фокуса поле 
  очищается  
<img src="https://raw.githubusercontent.com/1234ru/phone-formatter/master/docs/blank-input.gif" width="250" align="center">

* если вводу не соответствует ни один шаблон, форматирование проводиться не будет

* в любом случае ввод посторонних символов (букв и пр.) подавляется

* при вводе цифр не с конца сохраняет позицию курсора (в отличие от многих других аналогичных решений, где при любом вводе курсор прыгает в конец)

Работающий пример находится в файле [docs/demo.html](docs/demo.html).
