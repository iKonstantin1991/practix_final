# Practix
Репозиторий объединяющий все сервисы онлайн кинотеатра

### Команды для запуска сервисов
```bash
cd ./infra
docker-compose --project-name practix up -d \
    --scale auth_jaeger=0 \
    --scale notify-celery-beat=0 \
    --scale notify-celery-worker=0 \
--build
```

1. Зарегистрировать content_service, group_service, notifications_service в auth
2. Cоздать суперпользователя
```bash
docker exec -it practix-auth_service-1 bash
python /home/app/auth_api/src/create_superuser.py
```
3. Назначить роли service на сервисы из п.1
