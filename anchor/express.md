# [Содержание](../README.md)

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

