# Practix
Репозиторий объединяющий все сервисы онлайн кинотеатра

### Команды для запуска сервисов
1. Создать все необходимые .env файлы (см. /infra/docker-compose.yml)
2. Запустить все сервисы
```bash
cd ./infra
docker-compose --project-name practix up -d \
    --scale auth_jaeger=0 \
    --scale notify-celery-beat=0 \
    --scale notify-celery-worker=0 \
--build
```
3. Зарегистрировать content_service, group_watch_service, notifications_service в auth
4. Cоздать суперпользователя
```bash
docker exec -it practix-auth_service-1 bash
python /home/app/auth_api/src/create_superuser.py
```
5. Назначить роли service на сервисы из п.1
6. Загрузить необходимые шаблоны уведомлений в сервис нотификации
