# [Содержание](../README.md)

## Подключение CSS

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
 
