# [Содержание](../README.md)
# План
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

---
