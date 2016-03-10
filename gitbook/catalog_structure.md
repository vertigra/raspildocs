# Соглашение по структуре каталогов и файлов документации в репозитарии

---

## Иерархия каталогов верхнего уровня

Каталоги верхнего уровня содержат дирректории которым соответствует пять основных 
веток репозитария документов.

``` explorer
raspildocs
 |
 |-gitbook (ветка "GitBook. Приемы работы")
 |-raspil_for_dev (ветка "Raspil. Для разработчиков.")
 |-raspil_for_users (ветка "Raspil. Для пользователей.")
 |-sw_for_dev (ветка "Cупер Окна. Для разработчиков.")
 |-sw_for_users (ветка "Cупер Окна. Для пользователей.")
```

Не следует изменять без **крайней необходимость** иерархию каталогов верхнего уровня.

## Иерархия файлов в каталогах верхнего уровня

``` explorer
raspildocs
 |
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
 |-book.json (build файл gitbook)
 |-README.md (file)
 |-SUMMRY.md (файл структуры меню)
```

Файл README.md преобразуется в файл index.html после сборки книги.

### Создание поддиректорий в каталогах верхнего уровня

