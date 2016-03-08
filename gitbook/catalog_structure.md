# Соглашение по структуре каталогов и файлов документации в репозитарии

---

### Иерархия каталогов верхнего уровня

Каталоги верхнего уровня содержат дирректории которым соответствует пять основных 
веток репозитария документов.

```
raspildocs
 |
 |-.vscode (служебные файлы Visual Studio Code)
 |-gitbook (ветка "GitBook. Приемы работы")
 |-raspil_for_dev (ветка "Raspil. Для разработчиков.")
 |-raspil_for_users (ветка "Raspil. Для пользователей.")
 |-sw_for_dev (ветка "Cупер Окна. Для разработчиков.")
 |-sw_for_users (ветка "Cупер Окна. Для пользователей.")
```

Не следует изменять без **крайней необходимость** иерархию каталогов верхнего уровня.

### Иерархия файлов в каталогах верхнего уровня  

```
raspildocs
 |
 |-.vscode (folder)
 |-gitbook (folder)
 |  |-README.md (file)
 |-raspil_for_dev (folder)
 |  |-README.md (file)
 |-raspil_for_users (folder)
 |  |-README.md (file)
 |-sw_for_dev (folder)
 |  |-README.md (file)
 |-sw_for_users (folder)
 |  |-README.md (file)
 |-.gitignore 
 |-book.json
 |-pax_global_header
 |-README.md
 |-SUMMRY.md
```

