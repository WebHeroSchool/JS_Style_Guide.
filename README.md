<h3 id='link'> Правила оформления читабельного кода JS</h3>

## Оглавление

+ [Функции](#Первое)
+ [Строки](#Второе)
+ [Объекты](#Третье)
+ [Переменные](#Четвертое)
+ [Стрелочные функции](#Пятое)
+ [Массивы](#Шестое)
+ [Операторы равенства и идентичности](#Седьмое)
+ [Запятые](#Восьмое)
+ [Точки с запятой](#Девятое)
+ [Соглашение об именовании](#Десятое)
***
<h4 id='Первое'>Функции</h4>

###### Не объявляй функцию внутри цикла.
:x: ***~~плохая практика~~***
``` js
for (let i=10; i; i--) {
  (function() { return i; })();
}

while(i) {
  const a = function() { return i; };
  a();
}
``` 
:heavy_check_mark: ***хорошая практика***
``` js
const a = function() {};

for (let i=10; i; i--) {
  a();
}
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Второе'>Строки</h4>

###### Используйте одинарные кавычки '' для строк.
:x: ***~~плохая практика~~***
``` js
const name = "James Bond. James.";
const hello = "Say \"Hello world\"";
``` 
:heavy_check_mark: ***хорошая практика***
``` js
const name = 'James. James Bond.';
const hello = 'Say "Hello world"';
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Третье'>Объекты</h4>

###### Для создания объекта используйте литерал объекта {}. Так проще и читабельней.
:x: ***~~плохая практика~~***
``` js
const item = new Object();
``` 
:heavy_check_mark: ***хорошая практика***
``` js
const item = {};
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Четвертое'>Переменные</h4>

###### В ES6 не принято использовать var. Используйте const если не хотите чтобы значение переменной или ссылка на значение менялось. Во всех остальных случаях используйте let.
Используя const можно предотвратить перезаписи простых типов данных (string, number, boolean, null, undefined) или перезаписи ссылки на сложные типы данных (array, object, function). Улучшает понимание кода другими программистами, какие переменные можно менять, а какие нет.
Отказываясь от var получаем везде переменные с блочной областью видимости.
:x: ***~~плохая практика~~***
``` js
var a = 1;
var b = 2;
var count = 0;

if (true) {
    count += 1;
}
``` 
:heavy_check_mark: ***хорошая практика***
``` js
const a = 1;
const b = 2;
let count = 0;

if (true) {
    count += 1;
}
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Пятое'>Стрелочные функции</h4>

######  Когда нужно использовать функциональный литерал (например, передача анонимной функции как параметр другой функции), то используйте стрелочные функции.
Создается функция, которая будет выполняться в контексте текущего ```this```, а это то, что нам нужно в большинстве случаях.
Но если у вас очень сложная функция, то можете вынести эту логику и объявить отдельную функцию.

:x: ***~~плохая практика~~***
``` js
[1, 2, 3].map(function (x) {
    const y = x + 1;
    return x * y;
});
``` 
:heavy_check_mark: ***хорошая практика***
``` js
[1, 2, 3].map((x) => {
    const y = x + 1;
    return x * y;
});
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Шестое'>Массивы</h4>

###### Для создания массива используйте литерал массива []. Так проще и читабельней.


:x: ***~~плохая практика~~***
``` js
const items = new Array();
``` 
:heavy_check_mark: ***хорошая практика***
``` js
const items = [];
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Седьмое'>Операторы равенства и идентичности</h4>

###### Используйте ```===``` и ```!==``` вместо ```==``` и ```!=```.
При сравнивании неявно выполняется приведение типов переменных. Чтобы избежать этой путаницы всегда используйте операторы ```===``` и ```!==```, которые сравнивают и значения, и типы выражений.
:x: ***~~плохая практика~~***
``` js
false == 0;  // true
false == ''; // true
``` 
:heavy_check_mark: ***хорошая практика***
``` js
false === 0;  // false
false === ''; // false
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Восьмое'>Запятые</h4>

###### Скажите нет запятым в начале строки.
:x: ***~~плохая практика~~***
``` js
const story = [
      once
    , upon
    , aTime
];

const hero = {
      firstName: 'Ada'
    , lastName: 'Lovelace'
    , birthYear: 1815
    , superPower: 'computers'
};

``` 
:heavy_check_mark: ***хорошая практика***
``` js
const story = [
    once,
    upon,
    aTime,
];

const hero = {
    firstName: 'Ada',
    lastName: 'Lovelace',
    birthYear: 1815,
    superPower: 'computers',
};
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Девятое'>Точки с запятой</h4>

###### Ставим в конце каждой инструкции.
:x: ***~~плохая практика~~***
``` js
(function () {
    const name = 'Skywalker'
    return name
})()
``` 
:heavy_check_mark: ***хорошая практика***
``` js
(() => {
    const name = 'Skywalker';
    return name;
}());
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**

<h4 id='Десятое'>Соглашение об именовании</h4>

######  Избегайте однобуквенные имена. Имена должны давать представление о том, что это такое.
:x: ***~~плохая практика~~***
``` js
function q() {
    // ...stuff...
}
``` 
:heavy_check_mark: ***хорошая практика***
``` js
function query() {
    // ..stuff..
}
``` 
&nbsp;
**[⬆ к оглавлению](#Оглавление)**