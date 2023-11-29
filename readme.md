Для начала работы с Git необходимо выпонить следующие действия:
1. Установить Git Bash на компьютер
2. Создать репозиторий
3. Зарегистрироваться на сайте GitHub
4. Создать защищенный обмен данными
5. Синхронизировать локальный и удалённый репозитории

1. Установка Git Bash для пользователей Windows
- Скачать установщик с официального сайта Git "https://git-scm.com/download/win"
- Запустить его
- Выбрать подходящие опции из предлагаемых мастером установки

После установки нужно произвести настройки Git.  
Для этого в консоли прописываем команды   
git config --global user.name  
git config --global user.email



2. Для создания репозитория необходимо прописать в консоли команду git init.

- Создадим папку на компьютере и присвоим ей название, например test    
В консоли выполняем команды:   
mkdir test   
cd test  
git init 

В созданную папку добавляем файлы, например readme.txt и todo.txt

Далее нам нужно добавить оба файла в список отслеживаемых Git. Для этого воспользуемся командой git add.  
В консоли выполняем команды:   
git add --all (для добавления всех файлов)  
git add readme.txt  
git add todo.txt  

Теперь оба наших файла являются отслеживаемыми Git. Далее необходимо сделать коммит всех файлов командой git commit.
В консоли выполняем команды:  
git commit - m "Описание изменения, либо описание добавляемого файла"


3. Регистрация на GitHub

Регистрацию нужно произвести на официальном сайте GitHub - "https://github.com/"
Далее заходим в свой профиль и выбираем графу "your repositories"
Пройдя в неё нажимаем зелёную кнопку "New" чтобы создать новый репозиторий. 
В графе "Repository name" вводим имя репозитория, например Test и жмём далее
Так как у нас уже создан локальный репозиторий находим графу "or push an existing repository from the command line"
В консоли заходим в нашу папку, где создан репозиторий - "Test"
Прописываем следующие консольные команды:   
git remote add origin https://github.com/User_name/Test.git  
  git branch -m main  
  git push -u origin main

Готово. Мы создали удалённый репозиторий на GitHub.

4. Создание защищенного обмена данными с GitHub

В консоли прописываем следующую команду:   
ssh-keygen -t ed25519 -C "e-mail, к которому привязан аккаунт на GitHub"

Если данный способ не сработает то можно попробовать другую команду:
ssh-keygen -t rsa -b 4096 -C "e-mail, к которому привязан аккаунт на GitHub"

Далее высветится сообщение где сохранить ключи, укажите место хранения. 
Программа запросит кодовую фразу. 
Это поле можно оставить пустым либо ввести кодовую фразу для вашего ключа.
После нужно нажать Enter 2 раза. 
Должно появится 2 файла - один с расширением .pub, а другой - без.

Теперь данные ключа с расширением .pub нужно скопировать в буфер обмена. 
Для этого пропишите следующие команды в консоли:
clip < ~/.ssh/id_ed25519.pub
или
clip < ~/.ssh/id_rsa.pub
Если данные команды не сработают, то можно увидеть содержимое файлов при помощт команд:
cat ~/.ssh/id_ed25519.pub
или
cat ~/.ssh/id_rsa.pub
И скопировать в буфер обмена данные из консоли. 

Переходим в профиль на сайте GitHub выбираем "settings" и находим "SSH and GPG keys"
В открывшейся вкладке выбираем "New SSH key"

В поле "Title" вводим название ключа, например Personal Key
В поле "Key type" выбираем "Authentication Key"
в поле "Key" скопируйте ваш ключ из буфера обмена.
Далее нажимаем "Add SHH key"

Если это первый раз когда вы используете Git, чтобы поделиться проектом на GitHub, появится предупреждение. 
Чтобы подтвердить подлинность сервера GitHub публикует ключи SHA256. 
Ключи можно проверить по данный ссылке: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints
Если ключ в консоли совпадает с тем, что увидите на сайте, значит сервер подлинный.
Чтобы продолжить введите в консоли "yes" и нажмите "Enter". 

Готово. Ваш ключ привязан к GitHub. 

5. Синхронизация локального и удалённого репозиториев

Откройте консоль и введите следующие команды: 
cd test
git remote add origin git@github.com:%ИМЯ_АККАУНТА%/test.git

Чтобы убедиться, что репозитории связаны введите команду в консоли:
git remote -v

Готово. Локальный и удалённый репозитории связаны. 

Чтобы синхронизировать оба репозитория необходимо ввести следующию команду:
git push -u origun main

Готово. Оба репозитория синхронизированны. 
