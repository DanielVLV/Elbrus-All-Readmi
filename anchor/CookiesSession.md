# [Содержание](../README.md)

## Регистрация Cookies,Session

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
  secret: 'keyboard cat', // вместо 'keyboard cat' пишем COOKIE_SEKRET если настроен файл .env
  resave: false,
  saveUninitialized: true
  cookie: {
    maxAge: 10 * 60 * 1000, // устанавливаем сколько живет кука
    httpOnly: false
  },
}
```
- В файле `.env` дописываем строку : `COOKIE_SEKRET=всякая всячина` а в графе `secret` в объекте `sessionConfig` пишем вместо `'keyboard cat' -> COOKIE_SEKRET`

```js
DB_URI=[dialect]://[user[:password]@][netlocation][:port][/dbname]
PORT = 3000
COOKIE_SEKRET=всякая всячина
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
