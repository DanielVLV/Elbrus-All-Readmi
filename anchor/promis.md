# [Содержание](../README.md)
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
