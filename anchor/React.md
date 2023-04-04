# [Содержание](../README.md)

## Создание приложения с помощью Create React App

### версия с JS

устанавливаем необходимые зависимости
- `npx create-react-app my-app` 
можно вместо названия `my-app` поставить `.` в таком случае проект развернется в корневой папке

### версия с TS
```js
npx create-react-app my-app --template typescript
```

Устанавливаем Реакт роутер дом

- `npm i react-router-dom`
 иногда требуется перезагрузка vscod чтобы он увидел все зависимости

Устанавливаем Redux и toolkit

- `npm install react-redux --save`

- `npm install @reduxjs/toolkit`


## Компоненты и их import

```js
// Pokemon.jsx
function Pokemon() {
  return 'some pokemon';
}
export default Pokemon;


// App.jsx
import React from 'react';
import Pokemon from './Pokemon';
function App() {
  return (
    <div className="App">
      <Pokemon />
    </div>
  );
}
```

## Проброс Props

```js
// Pokemon.jsx
import React from 'react';
function Pokemon({ name, weight, img }) {
  return (
    <>
      <h2>{name}</h2>
      <strong>
        Вес:
        {weight}
        гектограмм
      </strong>
      <img src={img} alt={name} />
    </>
  );
}
export default Pokemon;

// App.jsx
import React from 'react';
import Pokemon from './Pokemon';
function App() {
  return (
    <div className="App">
      <Pokemon
        name="Slowpoke"
        weight={360}
        img="https://bit.ly/2LkFfgI"
      />
    </div>
  );
}
export default App;
```

## Использование map, key

```js
// App.jsx
import React from 'react';
import Pokemon from './Pokemon';
function App() {
  const pokemons = [
    { name: 'Slowpoke', weight: 360, img: 'https://bit.ly/2LkFfgI' },
    { name: 'Pikachu', weight: 60, img: 'https://bit.ly/3co9xem' },
    { name: 'Psyduck', weight: 196, img: 'https://bit.ly/2Wldz1g' },
  ];
  return (
    <div className="App">
      {pokemons.map(({ name, weight, img }) => (
        <Pokemon
          key={name}
          name={name}
          weight={weight}
          img={img}
        />
      ))}
    </div>
  );
}
export default App;
```

## Испольщование тернарника

```js
// Pokemon.jsx
import React from 'react';
function Pokemon({ name, weight = false, img }) {
  return (
    <>
      <h2>{name}</h2>
      {
        weight
          ? (
            <strong>
              Вес:
              {weight}
              гектограмм
            </strong>
          )
          : <strong>Вес не определён</strong>
      }
      <img src={img} alt={name} />
    </>
  );
}
export default Pokemon;
```

## Синтаксис и функционал useState

```js
// Pokemon.jsx
import React, { useState } from 'react';
const weightStep = 50;
function Pokemon({ name, weight, img }) {
  const [ currentWeight, setCurrentWeight, ] = useState(weight);
  function addWeight() {
    setCurrentWeight((x) => x + weightStep);
  }
  function removeWeight() {
    setCurrentWeight((x) => x - weightStep);
  }
  return (
    <>
      <h2>{name}</h2>
      <strong>
        Вес:
        {currentWeight}
        гектограмм
      </strong>
      <button onClick={addWeight} type="button">
        Потолстеть
      </button>
      <button onClick={removeWeight} type="button">
        Похудеть
      </button>
      <img
        width={96 * (currentWeight / weight)}
        src={img}
        alt={name}
        style={{ display: 'block' }}
      />
    </>
  );
}
export default Pokemon;
``` 

## Использование useEffect

```js
// App.jsx
import React, { useState, useEffect } from 'react';
function App() {
  const [date, setDate] = useState(new Date());
  useEffect(() => {
    const timer = setTimeout(() => setDate(new Date()), 1000);
    return () => clearTimeout(timer);
  }, [date]); /*обязательно должен быть массив зависимости, 
  если его оставить пустым, то useEffect выполниться 1 раз*/
  return (
    <div className="App">
      {date.toLocaleString()}
    </div>
  );
}
export default App;
```