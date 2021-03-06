# Настройка GitHib для работы с репозитарием документов #

---

## Рабочее окружение ##

* Windows 10 (x32)
* [Git-2.7.2-32-bit.exe](https://git-scm.com/download/win)

### Действительно (проверялось) для ###

* Windows 10 (x 64)
* [Git-2.7.4-64-bit.exe](https://git-scm.com/download/win)

## Настройка git c авторизацией по SSH без ключа passphrase ##

С помощью команды "git clone" скопировать репозитарий в локальную дирректорию.

1. Проверить наличие SSH ключей.

 ```bash
  $ ls -al ~/.ssh
 ```

 Рublic ключи по умолчанию имеют одно из указанных ниже имен

    * id_dsa.pub
    * id_ecdsa.pub
    * id_ed25519.pub
    * id_rsa.pub

1. Если ключей нет то следует их создать

 ```bash
  $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com
 Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
 ```

 Согласиться с местоположением файлов по умолчанию

 ```bash
 Enter passphrase (empty for no passphrase): [Type a passphrase]
 Enter same passphrase again: [Type passphrase again]
 ```

 Вводим пароль защищающий приватный ключ (два раза).

 *Внимание! Если планируется использование Visual Studio Code с паролем passphrase то требуется дополнительная настройка (описано ниже) *

1. После чего следует запустить ssh-agent

 ```bash
 Git Bash

  $ eval "$(ssh-agent -s)"

 Git for Windows

  $ eval $(ssh-agent -s)
 ```

1. Далее следует указать наши SSH ключи, SSH агенту

 ```bash
  $ ssh-add ~/.ssh/id_rsa
 ```

1. В настройках **профиля** (Setting) на GitHub.com в секции SSH keys следует добавить public ключ.

 *Не путать с настройками репозитария *

    * Нажимаем New SSH key
    * В поле Title указываем имя машины которой принадлежит public key
    * В поле key копируем содержания файла ~/.ssh/id_rsa.pub  
    (*Для Windows 10 (x64) + Git-2.7.4 команда clip у меня не работает, можно открыть
    файл ~/.ssh/id_rsa.pub блокнотом и **полностью** скопировать его содержимое*)

 ```bash
      $ clip < ~/.ssh/id_rsa.pub
 ```

    * Жмем Add SSH key

1. После чего нужно добавить GitHub.com в ~/.ssh/known_hosts

 ```bash
  $ ssh -T git@github.com
 ```

1. Проверяем протокол авторизации находясь в корне репозитария

 ```bash
  $ cd ~/path_to_repository
  $ git remote -v
 ```

 Вывод команды при авторизации по HTTPS

 ```bash
  $ https://github.com/USERNAME/OTHERREPOSITORY.git`
 ```

 Вывод команды при авторизации по SSH

 ```bash
  $ git@github.com:USERNAME/OTHERREPOSITORY.git
 ```

 Для корректной работы нам необходимо переключиться в режим авторизации по SSH (если вывод команды соответсвует HTTPS)

 ```bash
  $ git remote set-url origin git@github.com:USERNAME/OTHERREPOSITORY.git
 ```

1. Далее необходимо задать поведение команды "git push" по умолчанию.

 ```bash
  $ git config --global push.default simple
 ```

 (изменения отправляются только из текущей ветки в ветку с тем же именем, в случае если локальная ветка назначена для интеграции с удалённой веткой)

1. Для учета статистки комитов на графике contributors необходимо *обязательно* задать user.email тот же что указан в primary GitHub email
 address в настройках профиля на GitHub.com

 ```bash
  $ git config --global user.email "your_email@example.com"
 ```

 Имя пользователя задается командой (опционально)

 ```bash
  $ git config --global user.name "your_user_name_on_git_hub"
 ```

1. Тест (команда "git commit" без указанного пароля passphrase)

 ```bash
 $ touch tested_file
 $ git add tested_file
 $ git commit -m "Tested file commit

 [master 0ce57ec] Tested file commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 tested_file

 $ git push origin master
 ```

## Дополнительная настройка GitBash и Visual Studio Code с паролем passphrase ##

Для того что бы не вводить пароль passphrase каждый раз при команде "git push" необходимо произвести
действия описанные ниже.

Настройка GitBush

1. Указать пользователя на GitHub.com

 ```bash
 $ ssh -T billy.anyteen@github.com

 Hi username! You've successfully authenticated...
 ```

1. Проверить прикреплен ли открытый ключ к учетной записи

 ```bash
 Для версии OpenSSH 6.7 и старше
 $ ssh-add -l

 Для версии OpenSSH 6.8 и новее
 $ ssh-add -l -E md5
 ```

 После этого команда git push в GitBash должна проходить без запроса пароля passphare

Visual Studio Code

При запуске Visual Studio Code обычным способом встроенный клиент git работать не будет (ошибка Permission denied (publickey)).
Для того что бы он работал необходимо запустить Visual Studio Code следущим способом:

Открыть Git CMD и набрать следующие команды

```cmd
C:\Users\your_user_name> start-ssh-agent

Found ssh-agent at 2332
Found ssh-agent socket at /tmp/ssh-z4dlWUinmVkV/agent.4016

C:\Users\your_user_name> code (вызывает Visual Studio Code)
```

## Полезные команды ##

После добавления папки или файла в .gitignore необходимо также удалить его из индекса
с помощью команды `git rm --cached file_name`.
Например:

```bash
git rm --cached .gitignore
```

## Ссылки ##

[SSH Setting on GitHub.com](https://help.github.com/categories/ssh/)

[Релиз распределенной системы управления исходными текстами Git 1.8.0 ](Релиз распределенной системы управления исходными текстами Git 1.8.0 )
