# Первоначальная настройка Tortoisehg #

---

## Рабочее окружение ##

* Операционная система Windows 10 (x64)
* tortoisehg-3.7.2-x64.msi

### Действительно (проверялось) для ###

* Операционная система Windows 10 (x 32)
* tortoisehg-3.7.1-x86.msi

## Инсталяция ##

1. Устанавливаем tortoisehg
1. Запустить clone
1. После ошибки warning: Unexpected Fingerprint or Certificate not verified web.cacertsd будет следовать hostfingerprints
 подключаемого хоста (например 92:CC:DA:46:71:F8:89:CF:9E:F4:3F:17:3B:2B:C0:3A:8C:76:56:53).
1. Добавить в mercurial.ini (C:\Users\user_name) секцию

 ```xml
 [hostfingerprints]
 example.org = 92:CC:DA:46:71:F8:89:CF:9E:F4:3F:17:3B:2B:C0:3A:8C:76:56:53
 ```

 example.org - адрес репозитария

1. Создать дирректорию на жестком диске и клонировать туда репозитарий

## Ссылки ##

Скачать torstiehg можно [здесь](http://tortoisehg.bitbucket.org/download/index.html)