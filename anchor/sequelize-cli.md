# [Содержание](../README.md)
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
  },
 onDelete: 'cascade',
},
```

Для таблицы, где прописан foreignKey, нужно в ассоциациях прописать:

```js
this.belongsTo(models.Model, { foreignKey: "modelId" }); //много к одному
```

Для таблицы, на которую ссылается зависимая нужно прописать в зависимости от типа связи либо `hasOne`, либо `hasMany`

```js
this.hasMany(models.Model, { foreignKey: "modelId" }); //один к многим
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
const { Model } = require("./db/models");

async function create() {
  const result = await Model.create({ field1: value1, field2: value2 });
  return result;
}
```

### Получение информации

```js
const { Model, AnotherModel } = require("./db/models");

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
const { Model } = require("./db/models");

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
const { Model } = require("./db/models");

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
