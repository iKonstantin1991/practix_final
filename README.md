# Practix
Репозиторий объединяющий все сервисы онлайн кинотеатра

### Команды для запуска сервисов
```bash
cd ./infra
docker-compose --project-name practix up -d \
    --scale auth_jaeger=0 \
--build
```

1. Зарегистрировать content_service 
2. Зарегистрировать group_service
3. Cоздать суперпользователя
```bash
docker exec -it practix-auth_service-1 bash
python /home/app/auth_api/src/create_superuser.py
```
4. Назначить роли service на сервисы

