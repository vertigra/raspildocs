# Соглашение по форматированию кода Markdown в документах #

---

## Кодировка документов ##

**UTF-8 (без BOM) **

## Документация к Markdown ##

* [Блог разработчика John Gruber на daringfireball.net (en)](http://daringfireball.net/projects/markdown/)
* [Markdown на aboutslack.info (ru)](http://aboutslack.info/pages/development/markdown-cheatsheet.html)
* [Markdown на wiki](https://ru.wikipedia.org/wiki/Markdown)
* [Шпаргалка по Markdown](markdown_cheatsheet.md)

[Плагин для отслеживания ошибок в разметке Markdown](development_environment/components/markdowlintext_plugin.md)

## Заголовок статьи ##

```markdown
# Название статьи #
(пустая строка)
---
(пустая строка)
    ```

На конце заголовка не должно быть точки.

## Подзаголовки в статье ##

```markdown

(пустая строка)

## Подзаголовок ##

(пустая строка)
    ```

На конце заголовка не должно быть точки.

## Коментарии/todo ##

```markdown
(пустая строка)
<!-- todo сделать что-нибудь -->
(пустая строка)
    ```

## Оформление простых блоков кода ##

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


