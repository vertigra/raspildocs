# Соглашение по форматированию кода Markdown в документах

---

## Документация к Markdown

* [Блог разработчика John Gruber на daringfireball.net (en)](http://daringfireball.net/projects/markdown/)
* [Markdown на aboutslack.info (ru)](http://aboutslack.info/pages/development/markdown-cheatsheet.html)
* [Markdown на wiki](https://ru.wikipedia.org/wiki/Markdown)
* [Шпаргалка по Markdown](markdown_cheatsheet.md)

<!--перенести -->

## Автоматизация отслеживания ошибок в разметке

Для отслеживания ошибок удобно использовать плагин Visual Studio Code 
[markdownlintext](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint).

Инстукция по установке с сайта разработчика

1. Open Visual Studio Code
1. Press Ctrl+P to open the Quick Open dialog
1. Type ext install markdownlint to find the extension
1. Press Enter or click the cloud icon to install it
1. Restart Visual Studio Code if prompted

[Инструкция по управлению расширениями Visual Studio Code](https://code.visualstudio.com/docs/editor/extension-gallery?pub=DavidAnson&ext=vscode-markdownlint)

## Заголовок статьи

```markdown
# Название статьи
(пустая строка)
---
(пустая строка)
    ```

На конце заголовка не должно быть точки.

## Подзаголовки в статье

```markdown

(пустая строка)

## Подзаголовок

(пустая строка)
    ```

На конце заголовка не должно быть точки.

## Коментарии/todo

```markdown
(пустая строка)
<!-- todo сделать что-нибудь -->
(пустая строка)
    ```

## Оформление простых блоков кода

Простые блоки кода отделяются блоком  /```langure_name `/ в начале блока и символами /```/ в конце. Например

    ```java
    if(i = 1){
        return false;
    }
    ```

* ` ```text ` - структура каталогов, пути файловой системы, ini содержимое файлов
* ` ```с ` - небольшие участки кода c#
* ` ```java ` - небольшие  учатстки кода java
* ` ```xml ` - конфигурационные файлы xml
* ` ```markdown ` - примеры разметки markdown
* ` ```cmd ` командая строка Widows
* ` ```bash ` - командная строка bash (используется в Git для windows)

## Оформление сложных блоков кода


