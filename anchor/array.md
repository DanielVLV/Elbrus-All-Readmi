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

## Итог:
---
| метод |	что делает? | мутирующий? | что принимает? | что возвращает? |
|-----|-----|-----|-----|-----|
| .push() | добавляет в конец | да | элементы, которые нужно добавить | длину нового массива
| .pop() | удаляет последний элемент | да | - | удаленный элемент |
| .unshift() | добавляет в начало | да | элементы, которые нужно добавить | длину нового массива |
| .shift() | удаляет первый элемент | да | - | удаленный элемент |
| .split() | разбивает строку на массив | нет | массив | новый массив |
| .join() | склеивает элементы массива в строку | нет | массив | строку |
| .slice() | "делает из массива подмассив, также используется для поверхностного копирования массива" | нет | начальный индекс (включительно) и конечный индекс (не включен) | "новый массив (кусок изначального)" |
| .splice() | удаляет элементы из массива, вставляет другие при необходимости | да | начальный индекс (обязательный параметр), кол-во элементов (которые необходимо удалить), элементы (которые нужно вставить) | массив удаленных элементов |
| .concat() | соединяет массивы | нет | метод применяется к массиву, элементы которого будут первыми, а в аргументах - остальные массивы | новый массив |
| .reverse() | переворачивает массив | да | - | тот же массив в обратном порядке |
| .filter() | "фильтрует массив (позволяет получить новый массив, отфильтровав элементы с помощью переданной колбэк-функции)" | нет | коллбэк ф-ию, а она - el — элемент массива в текущей итерации (обязательный параметр); index — индекс текущего элемента; arr — сам массив, который мы перебираем | новый массив, элементы которого удовлетворяют условию в колбэк функции |
| .map() | трансформирует массив (запускает для каждого элемента колбэк-функцию, которая может как-то изменить элемент) | нет | коллбэк ф-ию, а она - el — элемент массива в текущей итерации (обязательный параметр); index — индекс текущего элемента; arr — сам массив, который мы перебираем | новый массив (измененных элементов) |
| .some() | "проверяет массив (вызывает колбэк для каждого элемента, если хотя бы для одного элемента вернет true, то весь метод вернет true)" | нет | колбэк ф-ию (условие проверки) | true/false |
| .every() | "проверяет массив(вызывает колбэк для каждого элемента, если хотя бы для одного элемента вернет false, то весь метод вернет false)" | нет | колбэк ф-ию (условие проверки) | true/false |
| .reduce() | """сворачивает"" массив в результирующее значение (последовательно применяет ф-ию к каждому элементу, передавая ей текущее значение переменной, в которой накапливается результат (аккумулятора) и текущий обрабатываемый элемент)" | нет | "колбэк ф-ию с аргументами асс, cur, index, arr и «начальное значение» init (опционально)acc – аккумулятор, последний результат вызова функции, он же «промежуточный результат» cur – текущий (current) элемент массива, элементы перебираются по очереди слева-направо index – номер текущего элемента (не обязательно) arr – обрабатываемый массив (не обязательно) init - (initial - изначальный) - если есть, то на первом вызове acc === init, а если нет, то init равен первому элементу массива, а перебор начинается со второго" | одно значение (поэтому называется reduce) |
| .sort() | сортирует элементы массива  | да | без параметров сортирует элементы как строки, если нужен собственный порядок - принимает колбэк ф-ию с двумя параметрами (см. примеры) | новый массив (отсортированный) |
| .forEach() | "перебирает массив (более ""элегантный"" вариант цикла for)" | нет | колбэк ф-ию (callback(item, i, arr)) | ничего |
| .flat() | преобразует из многомерного массива в одномерный | нет | depth (необязательный) - на сколько уровней вложенности уменьшается мерность исходного массива (по умолчанию 1) | новый массив (с объединёнными в него подмассивами) |
---