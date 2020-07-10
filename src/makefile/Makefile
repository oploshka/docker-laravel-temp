.DEFAULT_GOAL := help
# Локальный docker-registry для образов
REGISTRY = registry.git.labs.lc:5000/e.lebed/test
# Выводит описание целей - все, что написано после двойного диеза (##) через пробел
help:
  @grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-16s\033[0m %s\n", $$1, $$2}'

##################################################
# Создание (build) сжатых (squashed) docker-образов и пуш (push) в docker-registry для использования других окружениях
# Для сжатия (squash) на хост машине должен быть установлен флаг "experimental"
# Для пуша нужно залогиниться в docker-registry
##################################################
dc-bsp-all : dc-bsp-redis dc-bsp-workspace dc-bsp-php-fpm dc-bsp-node-npm dc-bsp-memcached dc-bsp-nginx dc-push-images

dc-bsp-nginx: ## Создание сжатого docker-образа для контейнера nginx
  docker build -f nginx/Dockerfile --squash -t $(REGISTRY):nginx-ed-sq nginx

dc-bsp-memcached: ## Создание сжатого docker-образа для контейнера memcached
  docker build -f memcached/Dockerfile --squash -t $(REGISTRY):memcached-ed-sq memcached

dc-bsp-node-npm: ## Создание сжатого docker-образа для контейнера node-npm
  docker build -f node-npm/Dockerfile --squash -t $(REGISTRY):node-npm-ed-sq node-npm

dc-bsp-php-fpm: ## Создание сжатого docker-образа для контейнера php-fpm
  docker build -f php-fpm/Dockerfile --squash -t $(REGISTRY):php-fpm-ed-sq php-fpm

dc-bsp-redis: ## Создание сжатого docker-образа для контейнера redis
  docker build -f redis/Dockerfile --squash -t $(REGISTRY):redis-ed-sq redis

dc-bsp-workspace: ## Создание сжатого docker-образа для контейнера workspace
  docker build -f workspace/Dockerfile --squash -t $(REGISTRY):workspace-ed-sq workspace

dc-push-images: ## Пуш созданных docker-образов в docker-registry
  docker push $(REGISTRY)

####################################################################################################
# Управление контейнерами с помощью docker-compose (dc)
####################################################################################################
dc-build: ## Сборка docker-образов согласно инструкциям из docker-compose.yml
  docker-compose build

dc-up: ## Создание и запуск docker-контейнеров, описанных в docker-compose.yml
  docker-compose up -d

dc-down: ## Остановка и УДАЛЕНИЕ docker-контейнеров, описанных в docker-compose.yml
  docker-compose down

dc-stop: ## Остановка docker-контейнеров, описанных в docker-compose.yml
  docker-compose stop

dc-start: ## Запуск docker-контейнеров, описанных в docker-compose.yml
  docker-compose start

####################################################################################################
# Подключение к консоли контейнеров (контейнеры должны быть запущены)
####################################################################################################
console-workspace: ## Подключение к консоли контейнера workspace (пользователь www-data)
  docker-compose exec --user www-data workspace bash

console-nginx: ## Подключение к консоли контейнера nginx (пользователь root)
  docker-compose exec nginx bash

console-php-fpm: ## Подключение к консоли контейнера php-fmp (пользователь root)
  docker-compose exec php-fpm bash

console-node: ## Подключение к консоли контейнера node (пользователь www-data)
  docker-compose run --user www-data --rm node bash
