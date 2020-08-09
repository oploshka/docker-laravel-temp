+ скопировать .env.example.env в .env
+ поправить docker-compose.yml (удалить не нужное)
+ переименование site_name_1 и site_name_2 на примере site_name_1
    + важно: новое название должно быть в нижнем регистре 
    + реплейснуть site_name_1 на новое название проекта (к примеру api_project)
    + в файле /container/nginx/config/conf.d/site_name_1.conf поправить server_name - на имя домена
    + переименовать /container/nginx/config/conf.d/site_name_1.conf
+ удалить не нужные конфиги из /container/nginx/config/conf.d
    
