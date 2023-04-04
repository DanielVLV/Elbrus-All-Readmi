# [Содержание](../README.md)
# План
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
