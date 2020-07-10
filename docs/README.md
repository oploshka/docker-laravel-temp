

### Заускаем Docker
+ docker-compose up -d

### Проводим миграцию 
+ docker-compose exec e-forum-api php artisan config:cache
+ docker-compose exec e-forum-api php artisan migrate

### Создаем ключи для генерирования надёжных токенов доступа
+ docker-compose exec e-forum-api php artisan passport:install

### Генерируем ключи для получения доступа к токену
+ docker-compose exec e-forum-api php artisan passport:keys

### Создаем пользователя (для теста)
+ docker-compose exec e-forum-api php artisan passport:client

### Проверяем POST запрос на API
+ http://api.e-forum.local/api/ping

### Полезные Docker команды 
+ docker-compose exec e-forum-api php artisan config:cache
+ docker-compose exec e-forum-api php artisan cache:clear
+ docker-compose exec e-forum-api php artisan view:clear
+ docker-compose exec e-forum-api php artisan route:clear
+ docker-compose exec e-forum-api php artisan clear-compiled
+ docker-compose exec e-forum-api composer dump-autoload --optimize

### Работа с моделью
+ docker-compose exec e-forum-api php artisan make:model User -m
+ docker-compose exec e-forum-api php artisan make:migration create_users_table --create=users

### Создаем базовую аутентификацию (уже создано)
+ docker-compose exec e-forum-api composer require laravel/ui --dev
+ docker-compose exec e-forum-api php artisan ui vue --auth
+ docker-compose exec e-forum-api npm run dev
