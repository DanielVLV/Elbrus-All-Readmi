# [Содержание](../README.md)
# Объекты
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
