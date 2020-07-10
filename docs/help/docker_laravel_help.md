
## команды по laravel
### Выполнить команду внутри контейнера
+ docker-compose exec [container_name] php artisan config:cache
+ docker-compose exec [container_name] php artisan migrate

### Создаем ключи для генерирования надёжных токенов доступа
+ docker-compose exec [container_`name] php artisan passport:install

### Генерируем ключи для получения доступа к токену
+ docker-compose exec [container_name] php artisan passport:keys

### Создаем пользователя (для теста)
+ docker-compose exec [container_name] php artisan passport:client

### Полезные Docker команды 
+ docker-compose exec [container_name] php artisan config:cache
+ docker-compose exec [container_name] php artisan cache:clear
+ docker-compose exec [container_name] php artisan view:clear
+ docker-compose exec [container_name] php artisan route:clear
+ docker-compose exec [container_name] php artisan clear-compiled
+ docker-compose exec [container_name] composer dump-autoload --optimize

### Работа с моделью
+ docker-compose exec [container_name] php artisan make:model User -m
+ docker-compose exec [container_name] php artisan make:migration create_users_table --create=users

### Создаем базовую аутентификацию (уже создано)
+ docker-compose exec [container_name] composer require laravel/ui --dev
+ docker-compose exec [container_name] php artisan ui vue --auth
+ docker-compose exec [container_name] npm run dev
