# Настройка GitHib для работы с репозитарием документов 

--- 

### Рабочее окружение

* Windows 10 (x32)
* [Git-2.7.2-32-bit.exe](https://git-scm.com/download/win)

### Настройка git c авторизацией по SSH без ключа passphrase 

1. Проверить наличие SSH ключей.
 ```
 $ ls -al ~/.ssh
 ``` 
 Рublic ключи по умолчанию имеют одно из указанных ниже имен

 * id_dsa.pub   
 * id_ecdsa.pub   
 * id_ed25519.pub   
 * id_rsa.pub

2. Если их нет то следует их создать 
 
 > $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
 > $ Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]

 Согласиться с местоположением файлов по умолчанию
 
 > $ Enter passphrase (empty for no passphrase): [Type a passphrase]
 > $ Enter same passphrase again: [Type passphrase again]
 
 Вводим пароль защищающий приватный ключ (два раза).
 
 *Внимание! Если планируется использование Visual Stidio Code с паролем passphrase то требуется 
 дополнительная настройка (описано ниже) *
 
3. После чего следует запустить ssh-agent

 Git Bash
 > $ eval "$(ssh-agent -s)"

 Git for Windows 
 > $ eval $(ssh-agent -s)

4. Далее следует указать наши SSH ключи, SSH агенту

 > $ ssh-add ~/.ssh/id_rsa

5. Далее в настройках *профиля* (Setting) на GitHub.com в секции SSH keys следует добавить 
public ключ.

 * Нажимаем New SSH key
 * В поле Title указываем имя машины которой принадлежит public key
 * В поле key копируем содержания файла ~/.ssh/id_rsa.pub 
   > $ clip < ~/.ssh/id_rsa.pub
 * Жмем Add SSH key

6. После чего можно добавить GitHub.com в ~/.ssh/known_hosts

 > $ssh -T git@github.com

7. Проверяем протокол авторизации находяся в корне репозитария 

 > $ git remote -v

 Вывод команды при авторизации по HTTPS
 > $ https://github.com/USERNAME/OTHERREPOSITORY.git

 Вывод команды при авторизации по SSH
 > $ git@github.com:USERNAME/OTHERREPOSITORY.git

 Для корректной работы нам необходимо переключиться в режим авторизации по SSH (если вывод команды соответсвут HTTPS)
 > $ git remote set-url origin git@github.com:USERNAME/OTHERREPOSITORY.git

8. Далее необходимо задать поведение команды "git push" по умолчанию.

 > $ git config --global push.default simple

 (изменения отправляются только из текущей ветки в ветку с тем же именем, в случае если локальная ветка назначена для интеграции с удалённой веткой)

9. Для учета статистки комитов на графике contributors необходимо *обязательно* задать user.email тот же что указан в
primary GitHub email address в настройках профиля на GitHub.com

 > $ git config --global user.email "your_email@example.com"

 Имя пользователя задается командой (опционально)
 >$ git config --global user.name "your_user_name_on_git_hub"

10. Тест (команда "git commit" без указанного пароля passphrase)

 > $ touch tested_file   
 > $ git add tested_file   
 > $ git commit -m "Tested file commit"  
 ```
 [master 0ce57ec] Tested file commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 tested_file  
 ```
 > $ git push origin master

### Дополнительная настройка GitBash и Visual Studio Code с паролем passphrase

Для того что бы не вводить пароль passphrase каждый раз при команде "git push" необходимо произвести
деиствия описаные ниже

* Настройка GitBush

 1. Указать пользователя на GitHub.com   
 > $ ssh -T billy.anyteen@github.com    
 ```
 Hi username! You've successfully authenticated...
 ```
 
 2. Проверить прикреплен ли открытый ключ к учетной записи
  
   Для версии OpenSSH 6.7 и старше
   > $ ssh-add -l

   Для версии OpenSSH 6.8 и новее
   > $ ssh-add -l -E md5

 После этого команда git push d GitBash должна проходить без запроса пароля passphare

* Visual Studio Code

 При запуске Visual Studio Code обычным способом встроенный клиент
 git работать не будет (ошибка Permission denied (publickey)). Для того что бы он работал необходимо запустить 
 Visual Studio Code следущим способом:
  
  1. Открыть Git CMD и набрать следующие команды
  >start-ssh-agent
   ```
   Found ssh-agent at 2332
   Found ssh-agent socket at /tmp/ssh-z4dlWUinmVkV/agent.4016
   ```
   >code (вызывает Visual Studio Code)


### Ссылки

[SSH Setting on GitHub.com](https://help.github.com/categories/ssh/)

[Релиз распределенной системы управления исходными текстами Git 1.8.0 ](Релиз распределенной системы управления исходными текстами Git 1.8.0 )
