# [Содержание](../README.md)
## Установка tailwindcss в проекте.

- `npm install -D tailwindcss`
- `npx tailwindcss init`

Устанавливаем пакет для использования `.scss`
- `npm i sass`

Настройте пути к шаблону
Добавьте пути ко всем файлам вашего шаблона в файл `tailwind.config.js`. 
```js
module.exports = {
  content: ['./src/**/*.{js,jsx,ts,tsx}'],
  theme: {
    extend: {},
  },
  plugins: [],
};
```
Добавляем директивы @tailwind для каждого из слоев Tailwind в файл ./src/index.css.
```js
@tailwind base;
@tailwind components;
@tailwind utilities;
```
Что бы корректно отрабатывали деректории нужно настроить корневой `json` в нем дописываем строку:
```js
"files.associations": {"*scss": "postcss", "*module.scss": "postcss"},
```

После инициализации и настройки конфига.
Можно для удобства использования tailwindA css поставить себе несколько расширений:
- Tailwind CSS IntelliSense
- PostCSS Intellisense and Highlighting
- PostCSS Language Support

Эти расширения нужны для того чтобы у нас были подсказки классов для tailwindA и создания 
своих собственных классов.

### Пример как пользьвоваться sccs:
```js
.parent {
    @apply border 
    rounded-lg p-4
    text-center
    drop-shadow-lg;
&>h1 {
   @apply text-blue-600

    }
.button {
    @apply mt-2 bg-red-500
    rounded-lg px-4 py-0
    animate-bounce;
    }
}
```
## [Документация tailwind Css](https://tailwindcss.ru/docs/installation/)


