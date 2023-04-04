# [Содержание](../README.md)
# Дебаг

## Работа с консолью
Базовый вариант `console.log`

Базовые уровни информирования пользователя
- debug - отладочная информация, не должно буть на проде
- info - информирование о событии
- warn - предупреждение, о том, что что-то не в порядке, но ошибка обработана
- error - серьезные проблемы, программа отработала некорректно

[Подробнее о методах](https://markodenic.com/use-console-log-like-a-pro/)

[CSS для консоль лога](https://dev.to/annlin/consolelog-with-css-style-1mmp)

[Раскрасить текст в терминале](https://stackoverflow.com/questions/43528123/visual-studio-code-debug-console-colors)

Базовые примеры раскраски цвета в терминале
- console.log( "`\u001b[31m` Red message" );
- console.log( "\u001b[32m Green message" );
- console.log( "\u001b[33m Yellow message" );
- console.log( "\u001b[34m Blue message" );
- console.log( "\u001b[35m Purple message" );
- console.log( "\u001b[36m Cyan message" );
- console.log( "\u001b[0m Reset text and background color/style to default" );
