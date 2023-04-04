# Содержание

## Phase 1
## [Работа с массивами](./anchor/array.md)
## [Работа с Объектами](./anchor/object.md)
## [Работа с консолью Дебаг](./anchor/debag.md)
## [Работа со строками, регулярные выражения](./anchor/string.md)
## [Работа с гитом](./anchor/git.md)
## [Обьекты и Протатипы](./anchor/prototype.md)
## [Работа с классами](./anchor/class.md)
## [Работа с промисами](./anchor/promis.md)
## [Работа с SQL](./anchor/sql.md)
## [Работа с Базой Данных через sequelize](./anchor/sequelize.md)
- ## [Секвалайз модели работа через sequelize-cli](./anchor/sequelize-cli.md)
- ## [Секвалайз Создание связи many-to-many](./anchor/sequelizeManyToMany.md)
- ## [Общая информация по sequelize-intro](./anchor/SequelizeIntro.md)
## Phase 2
## [Шпаргалка про Express](./anchor/express.md)
## [Создание сервера Express](./anchor/HTTP.md)
## [Использование Middleware](./anchor/Middleware.md)
## [Создание файла .env](./anchor/env.md)
## [Использование Fetch](./anchor/Fetch.md)
## [Регистрация Cookies,Session](./anchor/CookiesSession.md)
## Phase 3
## [Создание приложения с помощью Create React App](./anchor/React.md)




<br>

# W1D2

# План Работа с Array {#Array-header}
- Array


## Методы массива


### unshift: 
```js
const arr = ["a", "b", "c"];
const res = arr.unshift("e");
console.log(arr); // ['e', 'a', 'b', 'c']
console.log(res); // 4
```
`unshift()` - Добавить элемент в начало массива. Мутирует исходный массив, возвращает длину массивы

### shift:
```js
const arr = ["a", "b", "c"];
const res = arr.shift();
console.log(arr); // ['b', 'c']
console.log(res); // 'a'
```
`shift()` - Извлечь элемент из начала массива. Мутирует исходный массив, возвращает элемент

### push:
```js
const arr = ["a", "b", "c"];
const res = arr.push("d");
console.log(arr); // ['a', 'b', 'c', 'd']
console.log(res); // 4
```
`push()` - Добавить элемент в конец массива. Мутирует исходный массив, возвращает длину массива

### pop:
```js
const arr = ["a", "b", "c"];
const res = arr.pop();
console.log(arr); // ['a', 'b']
console.log(res); // 'c'
```
`pop()` - Извлечь элемент с конца массива. Мутирует исходный массив, возвращает элемент

### split:
```js
const names = "Biba,Boba,Giga,Goga";
const res = names.split(",");
console.log(res); // ['Biba', 'Boba', 'Giga', 'Goga']
```
`split()` - Преобразовать строку в массив. Возвращает массив

### join:
```js
const arr = ['Biba', 'Boba', 'Giga', 'Giga'];
const res = arr.join("-");
console.log(res); // 'Biba-Boba-Giga-Giga'
```
`join()` - Преобразовать массив в строку. Возвращает строку

### slice:
```js
const arr = ["a", "b", "c", "d", "e"];
const res = arr.slice(1);
console.log(res); // ['b', 'c', 'd', 'e']
------
const res = arr.slice(2,4);
console.log(res); // ['c', 'd']
```
`slice(1)` - НЕ мутирует исходный массив. Вернуть новый массив с 1 индекса

`slice(2, 4)` - Вернуть новый массив начиная со 2 индекса и заканчивая 4 индексом (не включая его)

### splice:
```js
const arr = ["a", "b", "c", "d", "e"];
const res = arr.splice(1, 2);
console.log(arr); // ['a', 'd', 'e']
console.log(res); // ['b', 'c']
```
`splice(1, 2)` - Удалить 2 элемента с 1 индекса. Мутирует исходный массив, возвращает новый массив

### concat:
```js
const arr1 = ["Biba", "Boba"];
const arr2 = ["Giga", "Goga"];
const res = arr1.concat(arr2, "1", "2");
console.log(res); // ['Biba', 'Boba', 'Giga', 'Goga', '1', '2']
```
`concat(1, 2)` - Создать новый массив из нескольких. Возвращает новый массив

### reverse:
```js
const arr = ["a", "b", "c", "d", "e"];
const res = arr.reverse();
console.log(arr); // ['a', 'd', 'e']
console.log(res); // ['b', 'c']
```
`reverse()` - Переставить элементы массива в обратном порядке. Мутирует исходный массив, возвращает новый массив

---------------------------------------------------------------------

# W1D3

# Работа с Объектами
Структура в виде ключ-значение. 
Позволяет получить доступ к значению с помощью ключа

## Создание нового объекта
Литерал объекта
```js
const obj = {
  name: 'Biba',
  age: 32,
  gender: 'Helicopter'
}
```
Конструктор объекта, считается устаревшим
```js
const obj = new Object( {
  name: 'Biba',
  age: 32,
  gender: 'Helicopter'
})
```
Использование короткой нотации
```js
const name = 'Biba'
const age = 32
const obj = { name, age }
```

## Доступ к значениеям

```js
const obj = {
  name: 'Biba',
  age: 32,
  gender: 'Helicopter'
}

obj.name

obj['name']

const key = 'name'
obj[key]

const { name, age, ...obj2 } = obj
```

## Методы Object
- Object.keys() - возвращает массив ключей, которые есть в объекте
- Object.values() - возвращает массив значений из объекта
- Object.entries() - возвращает массив массивов ключ-значение

## Работа со свойствами объекта
```js
const obj = {
  name: 'Biba',
  age: 32,
  gender: 'Helicopter'
}
```
Проверка, что в объекте есть определенное поле
```js
'name' in obj
```
Добавление или изменение поля
```js
obj.field = 'new field'
```
Удаление поля
```js
delete obj.gender
```

## Перебор ключей
```js
for (let key in obj) {
 // key - текущий ключ
 // obj[key] - текущее значение
 if (obj.hasOwnProperty(key)) {
   console.log(key, obj[key])
 }
}

```

## Методы объекта
Нет контекста
```js
const obj = {
  name: 'Biba',
  sayHi: () => {
    console.log(`Всем привет`)
  }
}
```
Есть контекст
```js
const obj = {
  name: 'Biba',
  sayHi: function (){
    console.log(`Всем привет от ${this.name}`)
  }
}
```

## Чейнинг
```js
const library = {
  address: {
    city: 'Default city',
    street: 'default street'
  },
  personal: [
    {
      name: 'Biba',
      age: 43,
    },
    {
      name: 'Boba',
      age: 20,
    }
  ]
}

console.log(library?.books?.fantasy)
```

---------------------------------------------------------------------

# W1D4

# Дебаг

## Работа с консолью
Базовый вариант `console.log`

Базовые уровни информирования пользователя
- debug - отладочная информация, не должно буть на проде
- info - информирование о событии
- warn - предупреждение, о том, что что-то не в порядке, но ошибка обработана
- error - серьезные проблемы, программа отработала некорректно

[Подробнее о методах](https://markodenic.com/use-console-log-like-a-pro/)

[CSS для консоль лога](https://dev.to/annlin/consolelog-with-css-style-1mmp)

[Раскрасить текст в терминале](https://stackoverflow.com/questions/43528123/visual-studio-code-debug-console-colors)

Базовые примеры раскраски цвета в терминале
- console.log( "`\u001b[31m` Red message" );
- console.log( "\u001b[32m Green message" );
- console.log( "\u001b[33m Yellow message" );
- console.log( "\u001b[34m Blue message" );
- console.log( "\u001b[35m Purple message" );
- console.log( "\u001b[36m Cyan message" );
- console.log( "\u001b[0m Reset text and background color/style to default" );


---------------------------------------------------------------------

# W1D5

# Работа со строками, регулярные выражения

## Полезные функции
- indexOf() - возвращает индекс первого подходящего вхождения,
начиная с указанного индекса (-1 - при отсутствии совпадения)
- lastIndexOf() - аналогично indexOf(), 
поиск по строке ведётся от конца к началу, начиная с указанного индекса
- charAt() - возвращает символ на месте индекса
- charCodeAt() - возвращает номер символа в юникод на месте указаного индекса
- toLowerCase() - переводит строку в нижний регистр
- toUpperCase() - переводит строку в верхний регистр
- slice() - возвращает подстроку от первого до второго индекса
- substring() - возвращает подстроку от первого до второго индекса
- replace() - заменяет вхождение на новое значение
- replaceAll() - возвращает все вхождения на новое значение

**Примеры использования**
```js
let str = "Cтрока";
str.charAt(2); // "р"
str.charCodeAt(2); // 1088 - номер символа Юникода
str.toLowerCase(); // "строка"
str.toUpperCase(); // "СТРОКА"

str.indexOf("id"); // 1 -> "Widget with id"
str.indexOf("id", 6); // 12 -> "Widget with id" (начало поиска с 6го символа)
str.lastIndexOf("id"); // 12 -> "Widget with id"

str = "Просто пример";
const s1 = str.slice(7);    // "пример"
const s2 = str.slice(-6, -3); // "при"
const s3 = str.substring(7);    // "пример"
const s4 = str.substring(3, 6); // "сто"

str = "JavaScript такой такой простой!";
str.replace("такой", "не"); // "JavaScript не такой простой!"
str.replace(/такой/g, "не"); // "JavaScript не не простой!"
str.replaceAll(/такой/, "не"); // "JavaScript не не простой!"
```

## Работа со строками
Можно использовать любые кавычки
```js
"Это строка";
'Это тоже строка';
```
Экранирование символов
```js
'Hello, \n\t world!';
'Hello \'my\' world!';
'Это \u2014\x20 просто строка';
'Это строка с \'кавычками\'';
```
Строка по шаблону
```js
const name = 'Biba'
`Hello, ${name}!`
```

# RegExp

>У вас есть проблема.  
> 
>Вы решили использовать регулярные выражения, чтобы её решить.  
> 
>Теперь у вас две проблемы

[Статья на хабре](https://habr.com/ru/post/545150/)  
[Тестирование выражений](https://regex101.com/)

## Создание нового regexp
```js
const regexp1 = new RegExp("шаблон", "флаги");
const regexp2 = /шаблон/g;

const str = "Я люблю JavaScript!";
const regexp = /лю/;
str.search(regexp); // 2
str.search(/лю/);   // 2
```

## Флаги
- i (ignoreCase) - регистронезависимость. `А` и `а` - одно и то же
- g (global) - ищет все вхождения, иначе только первое
- m (multiline) - работает с несколькими строками

## Базовый функционал

### Набор символов
[] - набор допустимых символов  
Примеры
```js
/[123]/ //символ 1 или 2 или 3
/[0-9]/ //диапазон символов от 0 до 9
/[^0-9]/ // любой символ кроме диапазона символов от 0 до 9
```
Короткие записи диапазонов:
- . (точка) – любой символ 
- \d = [0-9]
- \D = [^0-9]
- \w = [a-zA-Z0-9_]
- \W = [^a-zA-Z0-9_]
- \s = [\t\n\v\f\r ]
- \S = [^\t\n\v\f\r ]
- \b - разделители слов

_В набор `[а-я]` не входит буква `ё`_

### Спец символы, которые нуждаются в экранировании:
`[ ] \ ^ $ . | ? * + ( )`
```js
/\[\]/ // ищет []
```

### Границы строки
- `^` - начало строки
- `$` - конец строки

### Квантификаторы
- `{n}` - ровно n вхождений
- `\d{6}` - срабатывает на 6 цифр подряд. [0-9]{6} = \d\d\d\d\d\d
- `{2,4}` - от 2 до 4 вхождений
- `{3,}` - 3 и более вхождения
- `+` = {1,}
- `*` = {0,}
- `?` = {0,1}

### Группы
Когда мы берем что-то в круглые скобки внутри регулярного выражения, 
мы создаем группу. Каждой группе присваивается номер, по которому 
к ней можно обратиться.
```js
const str = 'Hello Biba'
const regexp = /(Hello)/
const newStr = str.replace(regexp, '$1,')
```

### Просмотр вперед и назад
- `(?=шаблон)` - позитивный просмотр вперед
- `(?!=шаблон)` - негативный просмотр вперед
- `(?Б=шаблон)` - позитивный просмотр назад
- `(?шаблон)` - негаативный просмотр назад


---------------------------------------------------------------------


# W2D1

# Работа с гитом

[Про git flow](https://docs.google.com/document/d/1-3uqgKUOGAC5OYvIRQ37CcJ1yepnSWdJysfUZ5aQN58/edit)
## Базовые принципы

### Создание коммитов
- Один коммит - одна фича
- Имя коммита должно отображать изменения в коде
- Имя коммита должно быть лаконичным
- Для более подробного описания можно использовать блок описания коммита

### Работа с ветками
- Одна ветка - одна задача
- Не меняем главную ветку напрямую, все изменения через пулл реквесты
- Имя ветки отражает суть задачи
- Прежде чем пушить изменения надо обновить маин и влить в свою ветку

## Работа с гитом в процессе решения задачи
1. `git checkout -b yourBranchName`
2. Пишем код, который решает задачу
3. Коммитим все свои изменения
4. `git checkout main`
5. `git pull`
6. Возвращаемся в свою ветку `git checkout yourBranchName`
7. `git merge main`
8. Решаем конфликты, если они есть
9. Пушим в репозиторий `git push --set-upstream origin yourBranchName`

## Базовые команды

### Работа с коммитами и удаленным репозиторием

- `git add fileNames` - добавляет файлы для коммита
- `git comit -m 'message'` - коммит добавленные файлы с сообщением
- `git fetch` - запрашивает информацию о ветках с удаленного репозитория
- `git push` - отправляет данные на удаленный репозиторий
- `git pull` - получает данные с удаленного репозитория

### Работа с ветками

- `git checkout name` - переключамся на существующую ветку
- `git checkout -b name` - создаем новую ветку и переключаемся на нее
- `git branch` - получаем список доступных веток
- `git merge name` - запускает процесс слияния двух веток
- `git merge --continue` - продолжает процесс слияния после разрешения мердж конфликтов
- `git merge --abort` - сбрасывает прогресс слияния веток


---------------------------------------------------------------------


# W2D3

# План Обьекты и Протатипы
- Object
- Prototype

## Object
Объект может быть создан с помощью фигурных скобок `{…}` с необязательным списком свойств. Свойство – это пара «ключ: значение», где `ключ` – это строка (также называемая «именем свойства»), а `значение` может быть чем угодно.


Пример:
```js
const person = {
  name: 'Biba',
  age: 25,
};
const key = 'age'

console.log(person.name)
console.log(person[key])
```

---


## Проверка существования свойства, оператор «in»

```js
// "key" in object

const person = {
  name: 'Biba',
  age: 25,
};

console.log("age" in person) // true
console.log("city" in person) // false

```
---

## Object.key()
Метод Object.keys() возвращает массив из собственных перечисляемых свойств переданного объекта

```js
const person = {
  name: 'Biba',
  age: 25,
};

console.log(Object.keys(person)) // ['name', 'age']

```

## Object.values()
Метод Object.values() возвращает массив значений перечисляемых свойств объекта

```js
const person = {
  name: 'Biba',
  age: 25,
};

console.log(Object.values(person)) // ['Biba', '25']

```
---

## This
Значение this зависит от контекста вызова

```js
const person = {
  name: 'Biba',
  age: 25,
  say() {
    console.log(`Hi ${this.name}`)
  }
};

person.say() // Hi Biba

```
this ссылается на объект в котором он был вызван

```js
function f(){
  return this;
}
console.log(f())
// window - глобальный объект в браузере
// global - глобальный объект в Node
```
---

## Call()
Метод call() вызывает функцию с указанным значением this и предоставленными аргументами.

```js
function showThis (surname, age) {
  console.log('this.name', this.name);
  console.log('args..', surname, age);
}

const boba = {
  name: 'Boba',
};

showThis.call(boba, 'Bobach', 33);

```

## Apply()
Метод apply() вызывает функцию с указанным значением this и предоставленными аргументами в виде массива.

```js
function showThis (surname, age) {
  console.log('this.name', this.name);
  console.log('args..', surname, age);
}

const boba = {
  name: 'Boba',
};

showThis.apply(boba, ['Bobach', 33]);

```
## Bind()
Метод bind() создаёт новую функцию, которая при вызове устанавливает в качестве контекста выполнения this

```js
function showThis (surname, age) {
  console.log('this.name', this.name);
  console.log('args..', surname, age);
}

const boba = {
  name: 'Boba',
};

const newShowThis = showThis.bind(bob);
newShowThis('Bobach', 33);

```

## Prototype

Прототипы - это механизм, с помощью которого объекты JavaScript наследуют свойства друг от друга.

> Object.prototype

### Наследование в объектах

```js
function Person (name, age) {
  this.name = name;
  this.age = age;
}

// добавляем новый метод sayHi() в свойство prototype конструктора 
Person.prototype.sayHi = () => console.log('Hi!!')

function Student (age, name, language) {
  // наследуем свойства от Person
  Person.call(this, name, age);
  this.language = language;
}
// наследуем prototype Person
Object.setPrototypeOf(Student.prototype, Person.prototype)
```


---------------------------------------------------------------------

# W2D4

- Class

# Работа с классами

## Class
Классы в JavaScript были введены в ECMAScript 2015 и представляют собой синтаксический сахар над существующим в JavaScript механизмом прототипного наследования. 

---

Метод constructor — специальный метод, необходимый для создания и инициализации объектов, созданных, с помощью класса.

```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}

const square = new Rectangle(10, 10);
```

---

## Наследование классов extends

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} издаёт звук.`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name); // вызывает конструктор super класса и передаёт параметр name
  }

  speak() {
    console.log(`${this.name} лает.`);
  }
}
```

## Полиморфизм 
Полиморфизм -  может быть достигнут в том, что у каждого класса есть своя функция, которая (при вызове) выполняется корректно для любого объекта.

## Инкапсуляция 
Инкапсуляция — это объединение данных и методов, которые воздействуют на эти данные, так что доступ к этим данным ограничен извне, «инкапсуляция — это локальное хранение и защита и скрытие процесса состояния». В ООП это означает, что объект хранит свое состояние в приватном порядке, и только методы объекта имеют доступ для его изменения.


---------------------------------------------------------------------

# W3D1

# Ассинхронность, и примеры использования

TIMEOUT
function printText(message) {
console.log(message);
}
setTimeout(printText, 1000, "До скорой встречи");
// При выполнении вернёт id созданного таймера



INTERVAL
const people = ["Василий", "Алёна", "Максим", "Филат"];
function playLottery(players) {
const i = Math.floor(Math.random() * players.length);
console.log(`Победитель лотереи: ${players[i]}`);
}
const interval = setInterval(playLottery, 1000, people);
clearInterval(interval);


CALLBACK
Callback – функция обратного вызова
Функция, которая передана в другую функцию и может быть ей
вызвана в нужный момент времени, например, по завершению
работы.

ПРИМЕР
let btn = document.querySelector("button");
btn.addEventListener("click", function(e) {
console.log(e.target);
});


FS ASYNC
const fs = require("fs");
fs.writeFile(`file.txt`, `Just text\n`, () => {});
fs.writeFile(`file.txt`, `1\n`, () => {});
fs.writeFile(`file.txt`, `2\n`, () => {});
fs.writeFile(`file.txt`, `3\n`, () => {});
fs.writeFile(`file.txt`, `Oooops\n`, () => {});


FS CALLBACK
let fs = require("fs");
fs.writeFile(`file.txt`, `Just text\n`, () => {
fs.appendFile(`file.txt`, `Want more characters!\n`, () => {
fs.readFile(`file.txt`, "utf-8", (err, data) => {
console.log(data);
// Just text
// Want more characters!
//
});
});
});


ARGUMENTS
Arguments - псевдомассив аргументов
function getSomething(a, b) {
if(arguments.length === 2) {
console.log(`${a} or ${b}`);
} else {
let str = `${a} or ${b}.`;
for (let i = 2; i < arguments.length; i++) {
str += ` ${arguments[i]}`;
}
console.log(str);
}
}



setTimeout(() => {
   console.log(1);
 }, 0);

 console.log(2);
 console.log(3);
 console.log(4);


setTimeout(() => {
  console.log(1);
}, 1000);
setTimeout(() => {
  console.log(2);
}, 999);
setTimeout(() => {
  console.log(3);
}, 1001);


 let count = 0;
 const idIt = setInterval(() => {
   console.log(count);
   count++;
  if (count > 7) {
     clearInterval(idIt);
  }
 }, 1000);
 
 console.log(idIt);
function func(name) {
   console.log(name)
}
 setTimeout(func, 1000, 'Biba');

 console.log('start');
 let sum = 0;
 console.time('timer');
 setTimeout(() => {
   console.log('setTimeout');
 }, 1000);
 for (let i = 0; i < 1_000_000_000_0; i++) {
  sum += 1;
}
 console.timeEnd('timer');
console.log(sum);


---------------------------------------------------------------------

# W3D2

# Работа с промисами

# Promise
[Подробная информация](https://learn.javascript.ru/promise)

Конструкция, которая пришла на смену колбекам для асинхронных функций.
Имеют три состояния
- PENDING
- FULLFILED
- REJECTED

## Базовое использование
Принимает на вход функцию с двумя арументами:
- resolve - функция устанавливает промис в состояние fullfilled
- reject - функция, устанвливает промис в состояние rejected

Для работы с промисом использоуются три следующие функции:
- then - обработка положительного сценария
- catch - обработка ошибок
- finally - выполняется в самом конце
```js
const promise = new Promise((resolve, reject) => {
  if (isResultGood) resolve('good')
  else reject('bad');
})

promise
  .then((data) => console.log(data))
  .catch((error) => console.log(error))
  .finally(() => console.log('Promise end'))
```

## Chaining (цепочка промисов)
Предполагается что в каждом из then будет асинхронное действие

```js
const promise = new Promise((resolve, reject) => {
  // что-то асинхронное
  if (isResultGood) resolve('good')
  else reject('bad');
})

promise.then((data) => {
      //делаем что нибудь асинхронное
      return newData
    })
    .then((newData) => {
      //Делаем что-то асинхронное с новыми данными
      return newData2
    })
    .then((newData2) => {
      //Делаем просто что нибудь обычное
    })
    .catch((error) => console.log(error))
```

## Промиссификация
Промисификация – это когда берут асинхронную функциональность и делают для неё обёртку, возвращающую промис.
```js
const fs = require("fs");

const fsReadPromise = (filePath) => {
  const promise = new Promise((resolve, reject) => {
    fs.readFile("./text.txt", "utf8", (err, data) => {
      if (err) {
        reject(err);
      } else {
        resolve(data);
      }
    })
  })
}

fsReadPromise("./new.txt")
  .then(console.log)
  .catch((err) => {
      console.error('-----------ERROR-------------')
      console.error(err)
    })
```

## Полезные статические методы Promise
- `Promise.all([promise1, promise2])` - принимает массив промиссов, возврашает массив с выполненными промисами либо падает с ошибкой
- `Promise.allSettled([promise1, promise2])` - возврашает массив промиссов с их статусами после их выполнения
- `Promise.resolved(data)` - возвращает промис со статусом fullfilled
- `Promise.rejected(error)` - возвращает промис со статусом rejected
- `Promise.race([promise1, promise2])` - возвращает первый выполненный промис

## ASYNC/AWAIT
async - говорит о том, что функция вернет промис
await - говорит о том, что надо дождаться выполнения результата, прежде чем переходить к дальнейшему коду
```js
const fs = require("fs").promises;

async function asyncReadFile(filePath) {
  const data = await fs.readFile(filePath);
  console.log(data)
}
```


---------------------------------------------------------------------

# W3D3

# Работа с ASYNC/ AWAIT 

async function foo() {
console.log('Foooo');
}
console.log('Start');
foo();
console.log('Finish');
&&
async function foo() {
return new Promise((resolve) => {
console.log('Foooo');
resolve();
});
}
console.log('Start');
foo();
console.log('Finish');


# PROMISE && ASYNC/AWAIT


Async/Await - “обёртка” над Promises.
Async-функция всегда возвращает Promise.

console.dir((async() => {})());
console.log(await (async() => {})());
console.log(await (async() => 42)());
(async () => 42)()
.then(console.log);
(async () => {throw 'Ooops'})()
.catch(console.error);


# Примеры с лекции:

const fs = require('fs').promises


fs.readFile('./files/text.txt', 'utf8', (err, data) => {
  main(data)
})

function main (data) {
  console.log(data)
}


const data = fs.readFile('./files/text.txt', 'utf8')
data
  .then((text) => console.log(text))
  .catch((err) => console.log(err))
  .finally(() => console.log('the end'))


 ASYNC

async function main() {
  try {
    const data = await fs.readFile('./files/text.txt', 'utf8')
     const count = data.length
    // ..
    console.log(data);
  } catch (error) {
    console.log(error);
  } finally {
    console.log('the end')
  }
   try {
     const response = await axios('https://domen.com')
   } catch (error) {
    console.log(error);
   }
}
main()


console.log(1);
async function main() {
  console.log(2);
  const data = await fs.readFile('./files/text.txt', 'utf8')
  console.log(3);
  console.log(data);
}
console.log(4);
main()
console.log(5);


async function main () {
  try {
    const data = await fs.readFile('./files/text.txt', 'utf8')
    return data
  } catch (error) {
    console.log(error)
  }
}

const result = main()
result.then((data) => console.log(data))

 async function prom() {
  const text = await main()
  console.log(text);
 }
 prom()
 
 
---------------------------------------------------------------------
 
 
# W3D4

# Работа с SQL

Декларативный язык, применяемый для создания, модификации и управления данными в реляционной системе управления базами данных (РСУБД).

В круг ответственности SQL входит добавление данных, извлечение по запросу, обновление и их удаление, а также создание и изменение схемы реляционной БД и контроль прав доступа к данным.

## Часто используемые типы данных

- `serial`: представляет автоинкрементирующееся числовое значение, которое занимает 4 байта и может хранить числа от 1 до 2147483647. Значение данного типа образуется путем автоинкремента значения предыдущей строки. Поэтому, как правило, данный тип используется для определения идентификаторов строки.
- `integer`: хранит числа от -2147483648 до +2147483647. Занимает 4 байта. Имеет псевдонимы int и int4.
- `double precision`: хранит числа с плавающей точкой из диапазона от 1E-307 до 1E+308. Занимает 8 байт. Имеет псевдоним float8.
- `character varying(n)`: представляет строку из фиксированного количества символов. С помощью параметра задается максимальное количество символов в строке. Имеет псевдоним varchar(n).
- `timestamp` или `timestamptz`: хранит дату и время. Занимает 8 байт. Для дат самое нижнее значение - 4713 г до н.э., самое верхнее значение - 294276 г н.э.
- `boolean` может хранить одно из двух значений: true или false.

## Работа с БД из консоли

Выполняем команду `psql` чтобы попасть в консольного клиента PostgrsQL
Чтобы создать пользователя воспользуйтесь командой  
`CREATE USER test_user WITH password 'qwerty';`

Чтобы создать базу используется команда `CRЕATE DATABASЕ`,
а ее владелец назначается с помощью параметра `OWNЕR`  
`CREATE DATABASE test_database OWNER test_user;`

Можно также дать пользователю права на существующую базу  
`GRANT ALL privileges ON DATABASE test_db TO test_user;`

Для удаления базы данных можно воспользоваться командой  
`DROP DATABASE test_db;`

## Работа со структурой БД

Вы можете создать таблицу, указав её имя и перечислив все имена столбцов и их типы:

```sql
CREATE TABLE students (
    id serial PRIMARY KEY,
    nаme varchar(80),
    age integer
);
```

Добавление нового поля в таблицу

```sql
ALTER TABLE students
ADD email varchar(20);
```

Связывание двух таблиц через айди

```sql
ALTER TABLE students ADD FOREIGN KEY (`group_id`) REFERENCES groups;
```

Для удаления таблицы
`'DROP TABLE jockeys'`

## Получение данных

Получение всех данных из таблицы студенты  
`SELECT * FROM students;`

Получение полей `name` и `age`  
`SELECT name, age FROM students;`

Получение всех данных для стеднтов, чей возраст меньше 18  
`SELECT * FROM students WHERE age < 18;`

Получение всех данных с сортировкой по возрастанию возраста  
`SELECT * FROM students ORDER BY age ASC;`

Получение всех данных с сортировкой по убыванию возраста
`SELECT * FROM students ORDER BY age DESC;`

Вычисление среднего возраста студентов  
`SELECT AVG(age) AS 'Средний возраст' FROM students;`

Получение данных из нескольких таблиц  
`SELECT * FROM students JOIN groups ON students.group_id = groups.id`

Таблица Employees. Получить список всех сотрудников у которых последняя буква в имени равна 'a'

`SELECT * FROM employees WHERE first_name LIKE '%a';`

Покажите список сотрудников (employees), чье имя начинается с "A"
`SELECT * FROM employees WHERE first_name LIKE 'A%';`

Покажите список всех счетов из Редмонда (Redmond), штат Вашингтон (WA)
`SELECT * FROM invoices WHERE billing_city LIKE 'Redmond'`

Покажите список всех счетов на сумму более $5,00 из г. Reno, шт. NV
`SELECT *  FROM invoices WHERE billing_state = 'NV' AND total > 5.00`

Покажите список каждого трека без композитора (composer) (Поиск строк которые пустые)
`SELECT * FROM  yourTable WHERE yourColumn IS NULL OR yourColumn = ''`

## Изменение данных

Вы можете изменять любые данные в таблице, указав условие:
`UPDATE students SET age = 26 WHERE name = 'Anna';`

## Удаление данных

Вы можете удалить запись из БД, например указав конкретный id записи  
`DELETE FROM students WHERE id = 1;`

Эта команда удалит всех студентов, чье имя = 'Anna'  
`DELETE FROM students WHERE name = 'Anna';`  
_Удаление не по id возможно, но считается плохой практикой_

## Типы ключей

- primary key - столбец, который в базе данных должен быть уникальным и, который используется для однозначной идентификации записи
- unique key - столбец или набор столбцов, для которого/которых значения не повторяются
- foreign key - это столбец в дочерней таблице, который в точности соответствует столбцу в родительской таблице, который определен как первичный (или уникальный) ключ, и ссылается на него.

Требования к ключам:

1. уникальность
2. долговечность
3. минимальность


---------------------------------------------------------------------

# W3D5

# Работа с Базой Данных через sequelize

[справка по SQL](./readme/README.SQL.md)  
[документация sequelize](https://sequelize.org/)

## Установка
Запускаем в терминале команду  
`npm install --save sequelize pg pg-hstore`
## Создание подключения
```js

const sequelize = new Sequelize('database', 'username', 'password', {
  host: 'localhost',
  dialect: 'postgres',
});
```

## Работа с запросами
Тест подключения
```js
try {
  await sequelize.authenticate();
  console.log('Connection has been established successfully.');
} catch (error) {
  console.error('Unable to connect to the database:', error);
}
```

Выполнение запроса  
```js
const [results, metadata] = await sequelize.query("SELECT * FROM students");
```

Параметры в запросе
```js
await sequelize.query(
 'SELECT * FROM projects WHERE status = ? AND lang = ?;',
 {
   replacements: ['active', 'js'],
   type: QueryTypes.SELECT
 }
);
```

Именованные параметры в запросе
```js
await sequelize.query(
 'SELECT * FROM projects WHERE status = :status AND lang = :lang;',
 {
   replacements: { status: 'active', lang: 'js' },
   type: QueryTypes.SELECT
 }
);
```
_Нужно указывать тот `type`, который используется в запросе_
 
 
---------------------------------------------------------------------

# W4D1


# Секвалайз модели работа через sequelize-cli 
# Sequelize Models

Добавление sequelize и sequelize-cli  
`npm install --save sequelize pg pg-hstore`  
`npm install --save-dev sequelize-cli`

## Настройка sequelize-cli

Пример файла `.sequelizerc`

```js
// .sequelizerc

const path = require("path");

module.exports = {
  config: path.resolve("db", "config", "database.json"),
  "models-path": path.resolve("db", "models"),
  "seeders-path": path.resolve("db", "seeders"),
  "migrations-path": path.resolve("db", "migrations"),
};
```

Инициализация sequelize создаст базовую структуру
в соответствии с описанием в файле `.sequelizerc`  
`npx sequelize-cli init`

## Открыть список возможностей функционал

`npx sequelize-cli --help`

## Работа с sequelize-cli

Создание новой модели:  
`npx sequelize-cli model:generate --name User --attributes firstName:string,lastName:string,email:string`
Создаст модель `User` и миграцию для нее с полями:

- `firstName` поле строкового типа
- `lastName` поле строкового типа
- `email` поле строкового типа

Работа с миграциями:

- `npx sequelize-cli migration:generate --name migration-skeleton` создает заготовку для миграции
- `npx sequelize-cli db:migrate` накатывает все новые миграции
- `npx sequelize-cli db:migrate:undo` откатывает последнюю миграцию

Работа с сидами:

- `npx sequelize-cli seed:generate --name demo-user` - создает заготовку для сидов
- `npx sequelize-cli db:seed:all` - накатывает все сиды
- `npx sequelize-cli db:seed:undo` - откатывает последний сид

## Создание связей one-to-one и one-to-many

Для поля типа `foreignKey` необходимо прописать в миграции следующую опцию

```js
references: {
  model: {
    tableName: 'tableName',
  },
  key: 'id'
}
```

Для таблицы, где прописан foreignKey, нужно в ассоциациях прописать:

```js
this.belongsTo(models.Model, { foreignKey: "modelId" });
```

Для таблицы, на которую ссылается зависимая нужно прописать в зависимости от типа связи либо `hasOne`, либо `hasMany`

```js
this.hasMany(models.Model, { foreignKey: "modelId" });
```

_modelId - имя foreignKey в зависимой таблицы_

## Полезные опции для миграций

- `defaultValue` - позволяет установить значение по умолчанию
- `allowNull` - может ли значение отсутствовать (null)
- `unique` - должны ли все записи быть уникальными
- `onDelete` - позволяет указать, что нужно делать при удалении записи, от которой зависит текущая

## Запросы с помощью моделей

[Подробная информация](https://sequelize.org/docs/v6/core-concepts/model-querying-basics/)

### Создание записи

```js
const { Model } = require("./db/model");

async function create() {
  const result = await Model.create({ field1: value1, field2: value2 });
  return result;
}
```

### Получение информации

```js
const { Model, AnotherModel } = require("./db/model");

async function read() {
  const result = await Model.findAll({
    where: { field: value },
    include: [AnotherModel],
  });
  return result.get({ plain: true });
}
```

### Обновление записи

```js
const { Model } = require("./db/model");

async function update() {
  const result = await Model.update(
    { field1: value1 },
    { where: { field2: value2 } }
  );
  return result;
}
```

### Удаление записи

```js
const { Model } = require("./db/model");

async function del() {
  const result = await Model.destroy({ where: { field2: value2 } });
  return result;
}
```

### Удаление всей таблицы

```js
const { Name } = require("./db/models");

async function nameDelite() {
  await Name.drop();
  console.log("Name table dropped!");
}
productDelite();
```


---------------------------------------------------------------------

# W4D2

# Создание связи many-to-many
Для связи many-to-many используется промежуточная таблица, которая содержит в себе айдишники из обеих таблиц.

В миграции для промежуточной таблицы нужно прописать рефернсы:  
```js
firstId: {
    type: Sequelize.INTEGER, 
    references: {
        model: {
          tableName: 'firstTable',
        },
        key: 'id'
    }
},
secondId: {
  type: Sequelize.INTEGER,
    references: {
    model: {
      tableName: 'secondTable',
    },
    key: 'id'
  }
},
```
В двух таблицах, которые необходимо связать прописываем в ассоциациях:
```js
// FirstModel
this.belongsToMany(models.SecondModel, {
  through: models.Something,
  foreignKey: 'firstId',
});

//SecondModel
this.belongsToMany(models.FirstModel, {
  through: models.Something,
  foreignKey: 'secondId',
});
```
Саму третью модель мы не меняем


---------------------------------------------------------------------

# W4D3 (Общая информация по siquelize)

# Sequelize intro

## Как начинали работу

1.  `npm init -y` - инициализируем проект node
1.  `npm i sequelize pg pg-hstore` - устанавливаем зависимости postgres
1.  `npm i -D sequelize-cli` - устанавливаем sequelize cli
1.  создаём файл `.sequelizerc`:

```Javascript
 const path = require('path');
 module.exports = {
 'config': path.resolve('db', 'config', 'config.json'),
 'models-path': path.resolve('db', 'models'),
 'seeders-path': path.resolve('db', 'seeders'),
 'migrations-path': path.resolve('db', 'migrations')
 };
```

1. `npx sequelize-cli init` - создаём структуру для работы с sequelize
1. В файле `config.json` изменили данные для БД (username, password, database, dialect) на свои. Обратите внимание, что мы ввели разные данные для development и test
1. Для того, чтобы sequelize следил за сидерами (не накатывались те сидеры, которые уже были добавлены в БД, аналогично миграциям),в файл `config.json` добавили строчки

```
    "seederStorage": "sequelize",
    "seederStorageTableName": "SequelizeData"
```

## Что сделали

1.  Создали модель командой `npx sequelize-cli model:generate --name User --attributes firstName:string,lastName:string,email:string` (изменили под себя)
    - Одновременно с этим создалась миграция
    - **Если поменяли что-то в модели - меняем и в миграции**
1.  Накатили миграцию `npx sequelize-cli db:migrate`
1.  Создали seeder командой `npx sequelize-cli seed:generate --name demo-user` (изменили под себя)

## На что обратить внимание

1.  Когда пишем seeder, поля `createdAt` и `updatedAt` нужно заполнить

1.  Когда пишем seeder, поля `createdAt` и `updatedAt` нужно заполнить самому `new Date()`

### Связи

**_Важно_**

Если в миграции вы указываете, что какое-то поле _таблицы А_ ссылается на _Таблицу В_, то на момент накатывания миграции с _Таблицей А_, уже должна существовать _Таблица В_. В обратном случае, вы получите ошибку `Table_name is not exist`.

![One-to-Many relation](readme_assets/1.png)  
_Таблица 1_. Связь One-to-Many.

1.  Чтобы создать связь (один ко многим), нужно:

    - в модели `Post`:

    ```JavaScript
         static associate(models) {
             this.belongsTo(models.User, {
                foreignKey: 'author',
             });
             }
    ```

    - в модели `User`:

    ```JavaScript
         static associate(models) {
            this.hasMany(models.Post, {
            foreignKey: 'author',
          });
          }
    ```

    - в миграции `create-post`:

    ```JavaScript
          author: {
          type: Sequelize.INTEGER,
          allowNull: false,
          references: {
              model: {
                  tableName: 'Users',
              },
          key: 'id',
          },
          }
    ```

## Миграции

Чтобы добвить новое поле в таблицу, нужно:

1. Создать миграцию командой `npx sequelize-cli migration:create --name new_column_in_user`

1. Изменить миграцию с использованием

   `JavaScript queryInterface.addColumn `

   и

   `queryInterface.removeColumn`

1. Добавить новое поле в модель `User`
1. Запустить миграцию `npx sequelize-cli db:migrate`
1. Создать миграцию командой

`npx sequelize-cli migration:create --name new_column_in_user`

1.  Изменить миграцию с использованием

`JavaScript queryInterface.addColumn `

и

`queryInterface.removeColumn `

1.  Добавить новое поле в модель `User`
1.  Запустить миграцию

`npx sequelize-cli db:migrate`

## Many to many

Для этого примера создан отдельный файл `appMany.js`, и отдельная бд, которая описана в файле config.json в части test. Чтобы запустить этот файл, нужно воспользоваться скриптом `npm run many`

### Идея

Есть три таблицы: Dogs, Cats и DogsCats. Многие собаки могут дружить с многими кошками. Связь между кошками и собаками описывается в таблице `Dogscats`.

![Many-to-Many relation](readme_assets/2.png)  
_Таблица 1_. Связь Many-to-Many.

### Модели

1. В модели Dogs нужно описать связь с многими котами через промежуточную таблицу:

   ```Javascript
   this.belongsToMany(Cat, { through: 'Dogscats', foreignKey: 'dog_id' });
   ```

1. В модели Cats нужно сделать аналогичную связь:

   ```Javascript
     this.belongsToMany(Dog, { through: 'Dogscats', foreignKey: 'cat_id' });
   ```

1. В модели Dogscats _ничего делать не нужно_

### Миграции

1. В миграции `dogscats` указываем, что столбцы `cat_id` и `dog_id` ссылаются на таблицы `Cats` и `Dog` соответсвенно

   ```Javascript
        dog_id: {
       type: Sequelize.INTEGER,
       references: {
         model: 'Dogs', // tableName
         key: 'id',
       },
        },
        cat_id: {
        type: Sequelize.INTEGER,
        references: {
         model: 'Cats', // tableName
         key: 'id',
       },
       },
   ```

1. В миграциях `Cats` и `Dogs` ничего делать не нужно

----------------------------------------------------------------------

## Шпаргалка по express

## Файл в корневой папке app.js или index.js

```js
// Подключение модуля fs на промисах
const fs = require('fs').promises;
// Подключение модуля для работы с путями
const path = require('path');
// Подключение библиотеки express
const express = require('express');

// Создание приложения express
const app = express();

// константа с портом
const PORT = 3000;

// Роут, отвечающий на запрос GET /
app.get('/', (req, res) => res.send('Hello!'));

// Роут, отвечающий на запрос GET /page1
app.get('/page1', (req, res) => res.send('Страница 1'));

// Роут, отвечающий на запрос GET /page2
app.get('/page2', (req, res) => res.send('Страница 2'));

// Роут, отвечающий на запрос GET /query-as-object
app.get('/query-as-object', (req, res) => 
  // Отправляем в ответ req.query as is
  res.send(req.query);
  
  //или
  
  // Отправляем в ответ 42
  res.send(String(42));
   
   //или
   
    // Отправляем в ответ JSON-объект
  res.json({
    message: 'Hello!',
  })
  
    //или
    
    // Отправляем в ответ query-строку
  const questionIndex = req.url.indexOf('?');
  res.send(questionIndex === -1 ? '' : req.url.slice(questionIndex));
);


// Роут, отвечающий на запрос GET /readme
app.get('/readme', async (req, res) => {
  // Составление пути до файла
  const readmePath = path.join(__dirname, '../../puzzles/puzzle135/README135.md');
  // Загрузка содержимого файла в формате UTF-8
  const readme = await fs.readFile(readmePath, 'utf8');
  // Отправляем в ответ содержимое README8
 res.send(readme);
});



// Запуск сервера по порту
app.listen(PORT, () => {
  console.log(`Server starting on PORT ${PORT}`);
});

```

----------------------------------------------------------------------

## W1D1


## Протокол HTTP 
Очень прост и состоит из двух частей:

- Заголовков запроса/ответа;
- Тела запроса/ответа.

# Express
Express представляет собой популярный веб-фреймворк, написанный на JavaScript и работающий внутри среды исполнения node.js.

## Установка и первый запуск
> npm init -y
>
> npm i express
>
> npx create-gitignore node
>
> npx eslint --init
>
> npm i -D nodemon morgan

> Работа с React SSR: `npm i @babel/core @babel/preset-env @babel/preset-react @babel/register react react-dom`

в файле json можно дописать 2 скрипта:

```js
 "start": "node app.js",
 "dev": "nodemon app.js"
```

Базовый скрит для запууска сервера на локальной машине

```js
const express = require('express');
const morgan = require('morgan');

const app = express();
const PORT = 3000;

app.use(morgan('dev'));

app.listen(PORT, () => {
  console.log(`Server starting on PORT ${PORT}`);
});
```
Что бы запустить сервер, в терминале пишем либо node название файла, 
либо если прописан скрипт: npm run dev

Теперь мы можем зайти в наше веб-приложение. Мы можем использовать хост `127.0.0.1`, или `localhost:3000`

Но предпочтительно заходить через `localhost:3000` чтобы избегать проблем с авторизацией. Из за политика с `cors`.

`morgan` - для логирование запросов между клиентом и сервером 

## HTTP methods: GET / POST

GET — метод для чтения данных с сайта. Например, для доступа к указанной странице. Он говорит серверу, что клиент хочет прочитать указанный документ. 

```js

app.get('/', function (req, res) {
  res.send('Hello World!');
});

```
POST — метод для отправки данных на сайт. Чаще всего с помощью метода POST передаются формы. Данный с формы находяс в теле запроса `body`

```js

app.post('/rofm', function (req, res) {
  const {title, text} = req.dody;
});

```

## SSR (Server Side Rendering)
это технология, которая позволяет, с помощью Node.js, запускать JavaScript код на сервере (а не в браузере как обычно) и готовый результат отправлять пользователю, избегая лишней нагрузки на его браузер и компьютер

### Работа с React SSR (вывод страниц)
Установим зависимости:

> npm i @babel/core @babel/preset-env @babel/preset-react @babel/register react react-dom

Создадим файл `.babelrc` и добавим скрипт

```js
// .babelrc

{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

Cоздадим файл `renderTemplate.js` который отвечает за отрисовку страниц

```js
require('@babel/register');
const ReactDOMServer = require('react-dom/server');
const React = require('react');

const renderTemplate = (reactElement, properties, response) => {
  const reactEl = React.createElement(reactElement, properties);

  const html = ReactDOMServer.renderToStaticMarkup(reactEl);

  response.write('<!DOCTYPE html>');
  response.write(html);
  response.end();
};

module.exports = renderTemplate;
```

Cоздадим два файла `Layout.jsx` и `Home.jsx`
```js
// Layout.jsx

const React = require('react');

function Layout({ title, children }) {
  return (
    <html lang="en">
      <head>
        <meta charSet="UTF-8" />
        <meta httpEquiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>React SSR</title>
      </head>
      <body>

        <header>
          <h1>Header</h1>
        </header>
        {children}
        <footer>
          <h1>Footer</h1>
        </footer>

      </body>
    </html>
  );
}

module.exports = Layout;
```
```js
// Home.jsx

const React = require('react');
const Layout = require('./Layout');

function Home(props) {
  return (
    <Layout>
      <h1>{props.title}</h1>
    </Layout>
  );
}

module.exports = Home;

```

## Query
Строка запроса (query) - фактически это часть запрошенного адреса, которая идет после знака вопроса `'?'`. Например, в запросе http://localhost:3000/about?id=3&name=Biba часть `id=3&name=Tome` представляет строку запроса.

```js

app.post('/rofm', function (req, res) {
  const {id, name} = req.query;
});

```

С помощью выражения `request.query` мы можем получить все параметры строки запрос в виде объекта javascript

## Params
Параметризированный запрос, объект req.params собирает данные на основе параметра. Используется для перехода на страницу с детальным описание

```js
app.get('/:userid', (req, res) => {
  console.log(req.params.userid) // "1"
})
```

----------------------------------------------------------------------

# W1D2

## Протокол HTTP 

Очень прост и состоит из двух частей:

- Заголовков запроса/ответа;
- Тела запроса/ответа.

# Express

Express представляет собой популярный веб-фреймворк, написанный на JavaScript и работающий внутри среды исполнения node.js.

# Middleware use()

Функции промежуточной обработки (middleware) - это функции, имеющие доступ к объекту запроса (req), объекту ответа (res) и к следующей функции промежуточной обработки в цикле “запрос-ответ” приложения. Следующая функция промежуточной обработки, как правило, обозначается переменной next.

```js
app.use((req, res, next) => {
  console.log('===== middleware ======');
  next();
});
```


Файл `render.js`

```js

require('@babel/register');
const ReactDOMServer = require('react-dom/server');
const React = require('react');

const render = (reactElement, properties, response) => {
  const reactEl = React.createElement(reactElement, properties);
  const html = ReactDOMServer.renderToStaticMarkup(reactEl);

  response.send(`<!DOCTYPE html>${html}`);
};

module.exports = render;

```
----------------------------------------------------------------------

# W1D3

1. Initialize

- `npm init -y`
- `npm i express dotenv`
- `npx create-gitignore node`
- `npx eslint --init`
- `npm i -D nodemon morgan`
- add to scripts in package.json
  ```
  "dev": "nodemon index.js --ext js,jsx"
  ```

2. Install React(ssr) Babel

- `npm i @babel/core @babel/preset-env @babel/preset-react @babel/register react react-dom`

- create .babelrc

  ```
  {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react"
    ]
  }
  ```

3. DB init sequelize

- `npm i sequelize sequelize-cli pg pg-hstore`

- create file .sequelizerc

  ```
  const path = require('path');
  module.exports = {
    'config': path.resolve('db', 'config', 'database.json'),
    'models-path': path.resolve('db', 'models'),
    'seeders-path': path.resolve('db', 'seeders'),
    'migrations-path': path.resolve('db', 'migrations'),
  };
  ```

- `npx sequelize init`

  ## Важно:

  Создать файл `.env` и `.env_example`. 
  Добавляем файл `.env` в `.gitignore`.

  В файле `.env_example` => прописываем настройки сервера: `DB_URI=[dialect]://[user[:password]@][netlocation][:port][/dbname]`

  В файле `.env` => прописываем свои личные настройки которые не пойдут в git.

  Соответственно в настройках сервера, удаляем всё лишнее.
```js
  "development": {
    "use_env_variable": "DB_URI",
    "dialect": "postgres"
  },
  ```
  В файле `.sequelizerc` в первой строке подкллючаем `require('dotenv').config()`

  ??? И в корневом файле тоже пишем первой строкой `require('dotenv').config()`

- `npx sequelize db:create`
- `npx sequelize model:generate` - generate all models
- don't forget references
- `npx sequelize db:migrate`

### ШАБЛОН файла index.js

```js
require('@babel/register');

require('dotenv').config();

const express = require('express');
const morgan = require('morgan');
const path = require('path');

const app = express();
const PORT = process.env.PORT ?? 3000;

app.use(express.urlencoded({ extended: true }));
app.use(express.json());

app.use(morgan('dev'));
app.use(express.static(path.join(process.cwd(), 'public')));

const indexRouter = require('./src/routes/index.routes');

app.use('/home', indexRouter);

app.get('/', (req, res) => { res.redirect('/home'); });

app.get('*', (req, res) => { res.redirect('/'); });

app.listen(PORT, () => {
  console.log(`listening on port${PORT}`);
});
```

### Tips

- Set path for static code, styles and assets.
  ```js
  app.use(express.static(path.join(process.cwd(), 'public')));
  ```

- To use `public` assets you need to remember that the `public` is the root. Example how to use `public`:
  - In `Layout`
  ```js
    <link rel="icon" type="image/x-icon" href="/assets/favicon.ico" />
    <link rel="stylesheet" href="/css/style.css" />
  ```
  - If you need a background in css:
  ```js
    background: url("/assets/tiger_pattern.jpg") repeat;
  ```
  - If you need a src in img tag:
  ```js
    <img src="/assets/user.jpg" className="card-img-top" alt="user" />
  ```
- How to send all props to the parent or child component

  ```js
  <Layout {...props}>
    ...
  </Layout>
  ```

- How to write a router
  - Structure
    ```
    - src
      - views
      - middleware
      - routers
        - user.router.js
      - index.js
  - In user.router.js

    ```
    ```js
    const router = require('express').Router();

    router.get('/', async (req, res) => {
      res.send("Hello User!");
    });

    module.exports = router
    ```

  - In index.js
    ```js
    const UserRouter = require('./routers/user.router');
    app.use('/<prefix>', UserRouter);
    ```
  - If prefix is set than you must take it in to account when   making calls to the router you need. Example: 
    ```js
    app.use('/users', UserRouter);
    ```
    Then when we make the call we must address `/users` to enter the router above.

- Middleware are set buy `app.use()`
  ```js
  app.use(express.json());
  app.use(express.urlencoded({ extended: true }));
  app.use(express.static(path.join(process.cwd(), 'public')));
  app.use((req,res,next)=>{
    next()
  });
  ```
  These are all middlewares. They change the request and/or the response object.
  How to use them, couple examples:
  - Global middleware. It will be invoked with every request.
  ```js
    app.use((req,res,next)=>{
    next()
    });
  ```
  - Router middleware. It will be invoked with every router request.
  ```js
  async function usersCount(req, res, next) {
    const count = await User.count();
    console.log(count);
    next();
  }
  
  app.use('/users', usersCount, UserRouter);
  ```
  - Endpoint middleware. It will be invoked with every specific endpoint request.
  ```js
    const router = require('express').Router();

    async function usersCount(req, res, next) {
      const count = await User.count();
      console.log(count);
      next();
    }

    router.get('/', usersCount,async (req, res) => {
      res.send("Hello User!");
    });

    module.exports = router
  ```

  - Local variables. There are two types of local variables, first is global and will be in `app.locals` and request variables `res.locals`. However, if you need to enter the global variables in your request, you can use `res.app.locals`
 
  

----------------------------------------------------------------------
 
# W1D4 
  
1. Initialize

- `npm init -y`
- `npm i express dotenv`
- `npx create-gitignore node`
- `npx eslint --init`
- `npm i -D nodemon morgan`
- add to scripts in package.json
  ```
  "dev": "nodemon index.js --ext js,jsx"
  ```

2. Install React(ssr) Babel

- `npm i @babel/core @babel/preset-env @babel/preset-react @babel/register react react-dom`

- create .babelrc

  ```js
  {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react"
    ]
  }
  ```

3. DB init sequelize

- `npm i sequelize sequelize-cli pg pg-hstore`

- create file .sequelizerc

  ```js
  const path = require('path');
  module.exports = {
    'config': path.resolve('db', 'config', 'database.json'),
    'models-path': path.resolve('db', 'models'),
    'seeders-path': path.resolve('db', 'seeders'),
    'migrations-path': path.resolve('db', 'migrations'),
  };
  ```

- `npx sequelize init`
- `npx sequelize db:create`
- `npx sequelize model:generate` - generate all models
- don't forget references
- `npx sequelize db:migrate`

### Tips

- Set path for static code, styles and assets.

  ```js
  app.use(express.static(path.join(process.cwd(), 'public')));
  ```

- To use `public` assets you need to remember that the `public` is the root. Example how to use `public`:
  - In `Layout`
  ```js
    <link rel="icon" type="image/x-icon" href="/assets/favicon.ico" />
    <link rel="stylesheet" href="/css/style.css" />
  ```
  - If you need a background in css:
  ```js
    background: url("/assets/tiger_pattern.jpg") repeat;
  ```
  - If you need a src in img tag:
  ```js
    <img src="/assets/user.jpg" className="card-img-top" alt="user" />
  ```
- How to send all props to the parent or child component

  ```js
  <Layout {...props}>
    ...
  </Layout>
  ```

- How to write a router

  - Structure
    ```
    - src
      - views
      - middleware
      - routers
        - user.router.js
      - index.js
    ```
  - In user.router.js

    ```js
    const router = require('express').Router();

    router.get('/', async (req, res) => {
      res.send("Hello User!");
    });

    module.exports = router
    ```

  - In index.js
    ```js
    const UserRouter = require('./routers/user.router');
    app.use('/<prefix>', UserRouter);
    ```
  - If prefix is set than you must take it in to account when making calls to the router you need. Example:
    ```js
    app.use('/users', UserRouter);
    ```
    Then when we make the call we must address `/users` to enter the router above.

- Middleware are set buy `app.use()`

  ```js
  app.use(express.json());
  app.use(express.urlencoded({ extended: true }));
  app.use(express.static(path.join(process.cwd(), 'public')));
  app.use((req,res,next)=>{
    next()
  });
  ```

  These are all middlewares. They change the request and/or the response object.
  How to use them, couple examples:

  - Global middleware. It will be invoked with every request.

  ```js
    app.use((req,res,next)=>{
    next()
    });
  ```

  - Router middleware. It will be invoked with every router request.

  ```js
  async function usersCount(req, res, next) {
    const count = await User.count();
    console.log(count);
    next();
  }

  app.use('/users', usersCount, UserRouter);
  ```

  - Endpoint middleware. It will be invoked with every specific endpoint request.

  ```js
    const router = require('express').Router();

    async function usersCount(req, res, next) {
      const count = await User.count();
      console.log(count);
      next();
    }

    router.get('/', usersCount,async (req, res) => {
      res.send("Hello User!");
    });

    module.exports = router
  ```

  - Local variables. There are two types of local variables, first is global and will be in `app.locals` and request variables `res.locals`. However, if you need to enter the global variables in your request, you can use `res.app.locals`

## Fetch methods

- GET - get all records
- POST - create a new record
- PUT(PATCH) - update a record

```js
  const obj = {name: 'foo', age: 44}

  PUT - send {name: 'fuu', age: 44}
  PATCH - send {age:33}
```

- DELETE - delete a record

### Fetch Response

If fetch request is sent then you must response with status code or json


----------------------------------------------------------------------

# W2D4 
 
1. Initialize

- `npm init -y`
- `npm i express dotenv`
- `npx create-gitignore node`
- `npx eslint --init`
- `npm i -D nodemon morgan`
- add to scripts in package.json
  ```
  "dev": "nodemon index.js --ext js,jsx"
  ```

2. Install React(ssr) Babel

- `npm i @babel/core @babel/preset-env @babel/preset-react @babel/register react react-dom`

- create .babelrc

  ```
  {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react"
    ]
  }
  ```

3. DB init sequelize

- `npm i sequelize sequelize-cli pg pg-hstore`

- create file .sequelizerc

  ```
  const path = require('path');
  module.exports = {
    'config': path.resolve('db', 'config', 'database.json'),
    'models-path': path.resolve('db', 'models'),
    'seeders-path': path.resolve('db', 'seeders'),
    'migrations-path': path.resolve('db', 'migrations'),
  };
  ```

- `npx sequelize init`
- `npx sequelize db:create`
- `npx sequelize model:generate` - generate all models
- don't forget references
- `npx sequelize db:migrate`

### Tips

- Local variables. There are two types of local variables, first is global and will be in `app.locals` and request variables `res.  locals`. However, if you need to enter the global variables in your request, you can use `res.app.locals`

1. Данные мы можем сохранить в глобальный объект нашего сервиса в `app.locals`

### Cookie, Session

- `npm i express-session`
- `npm i session-file-store`

Создать конфиг:
```js
const sessionConfig = {
  store: new FileStore(), // добавить после установки session-file-store
  secret: 'keyboard cat',
  resave: false,
  saveUninitialized: true
  cookie: {
    maxAge: 10 * 60 * 1000, // устанавливаем сколько живет кука
    httpOnly: false
  },
}
```

Добавляет middleware `use()`

```js
// index.js

const expressSession = require('express-session');
// для хранения даннах из куки
const FileStore = require('session-file-store')(expressSession);

// ...

app.use(expressSession(sessionConfig));
```

Добавить в скрипте `dev` добавить игнорирование для отслеживания nodemon 

```js
"dev": "nodemon src/index.js --ext js,jsx --ignore sessions",
```

### Пароль
- `npm i bcrypt` 
 

----------------------------------------------------------------------


# Создай новое приложение с помощью Create React App:

### версия с JS

устанавливаем необходимые зависимости
- `npx create-react-app my-app` 
можно вместо названия `my-app` поставить `.` в таком случае проект развернется в корневой папке

### версия с TS
```js
npx create-react-app my-app --template typescript
```

Устанавливаем Реакт роутер дом

- `npm i react-router-dom`
 иногда требуется перезагрузка vscod чтобы он увидел все зависимости

Устанавливаем Redux и toolkit

- `npm install react-redux --save`

- `npm install @reduxjs/toolkit`

----------------------------------------------------------------------


