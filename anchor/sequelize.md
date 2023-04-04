# [Содержание](../README.md)
# Работа с БД через sequelize

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
