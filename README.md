# Содержание
## [Создание сервера Express](./anchor/HTTP.md)
## [Использование Middleware](./anchor/Middleware.md)

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

> Работа с React SSR: npm i @babel/core @babel/preset-env @babel/preset-react @babel/register react react-dom

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
