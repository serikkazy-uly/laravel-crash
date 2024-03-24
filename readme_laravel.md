# Установка Laravel с использованием Docker Compose

Ссылка на [видео](https://www.youtube.com/watch?v=c6FbzmjC6oA).

- **USER 1000** - user
- **USER 0** - admin

**php-cli:** для создания файлов и т.п. / Для работы в терминале

**php-fpm** работает в связке с nginx - для работы сайта

### Команды:

```bash
docker-compose up --build -d

docker compose exec php-cli bash

composer create-project laravel/laravel example-app

exit

mv example-app/* ./
mv example-app/.* ./

rm -rf example-app/
```

### Настройка хоста:
```bash
localhost:8080
```

```bash
- sudo chmod 777 -R storage/
```
### Настройка БД:
```bash
- docker compose exec php-fpm bash
- php artisan
- php artisan migrate 
```

Если возникла ошибка!
`Illuminate\Acces denied`, то перейдите в

 /vendor/.env и на 16 строке укажите пароль:

```.env
DB__PASSWORD=`secret`.
```

Проверьте: 
```bash
php artisan migrate 
```
(Должно выйти сообщение `Nothing to migrate`)

### Настройка песочницы:
```bash
php artisan tinker
```
### Использование php-cli
```bash
- docker compose php-cli bash
- php artisan tinker  
```
!Cоздать тестовый файл TestController.php (его мы НЕ можем изменять!)

```bash
- docker compose php-cli bash
- php artisan make:controller TestingController (а его можем изменять)
```

```bash
- docker compose exec -u 0 php-cli bash
- php artisan tinker  
```
### Установить пакеты node:
```bash
- docker compose exec node npm install
- docker compose exec node npm run build
```
### Добавьте в файл vite.config.js:
```vite.config.js
server: {
    host: '0.0.0.0',
    port: 3000,
    open: false,
}
```

```bash
- docker compose exec node npm run dev
```
### Как проверить CSS ?
В файле /resourses/views/welcome.blade.php, на 17 строке перед:

```html
</head>
```
добавьте: 
```css
@vite('resources/css/app.css').
```


### Стартер кит (Регистрация аутентификация) Laravel Breeze
```bash
- make cli
- composer require laravel/breeze --dev
- php artisan breeze:install
- exit
- make npm-install
- make npm-build
```
<!-- try_files $uri $uri/ /index.php?$query_string; -->


php artisan make:model Note -m
change migration
php artisan migrate

php artisan make:factory NoteFactory --model=Note
php artisan migrate:refresh --seed 

php artisan make:controller NoteController --resource --model=Note


php artisan make:views note.index
php artisan make:views note.create
php artisan make:views note.edit
php artisan make:views note.show

touch resources/views/note/create.blade.php

----------

composer require laravel/ui
php artisan ui bootstrap --auth
docker compose exec node npm install
docker compose exec node npm run dev
php artisan migrate ????????????????


docker compose exec node npm install --sa
ve-dev vite laravel-vite-plugin

docker compose exec node npm run build