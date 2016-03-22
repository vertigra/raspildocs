# Автоматизация отслеживания ошибок в разметке #

---

## Инсталяция ##

Для отслеживания ошибок удобно использовать плагин Visual Studio Code [markdownlintext](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint).

Инстукция по установке с сайта разработчика

1. Open Visual Studio Code
1. Press Ctrl+P to open the Quick Open dialog
1. Type ext install markdownlint to find the extension
1. Press Enter or click the cloud icon to install it
1. Restart Visual Studio Code if prompted

## Настройка ##

В корень проекта нужно положить файл .markdownlint.json.  
Содержание файла

```json
{
    "MD009": { "br_spaces": 2},
    "MD013": { "line_length": 150}
}
```

"MD009": { "br_spaces": 2} - разрешает две пробела в конце строки (для переноса строки).  
"MD013": { "line_length": 150} - максимальная длина строки 150 символов (default: 80)


