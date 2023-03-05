# Содержание
## [Шпаргалка про Express](./anchor/express.md)
## [Создание сервера Express](./anchor/HTTP.md)
## [Использование Middleware](./anchor/Middleware.md)
## [Подключение CSS](./anchor/CSS.md)
## [Использование Fetch](./anchor/Fetch.md)

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
 
 
 
  
