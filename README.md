# Pulse Messenger

Полноценный local-first web messenger scaffold, созданный по загруженному master prompt: архитектура предусматривает production stack с PostgreSQL/Redis/MinIO/Prisma и realtime/WebRTC, а текущий runnable режим специально сделан без внешних npm-зависимостей, чтобы проект можно было запустить прямо из каталога на этой машине.

## Быстрый запуск

Требуется Node.js 20+.

```bash
npm run dev
```

Открой:

http://localhost:3000

## Что уже работает локально

- регистрация и вход через backend;
- persistent sessions в JSON database;
- поиск пользователей по username/имени/телефону;
- личные чаты;
- группы и каналы;
- realtime доставка сообщений через WebSocket;
- отправка/редактирование/удаление сообщений;
- реакции;
- загрузка изображений и файлов;
- голосовые сообщения через MediaRecorder;
- очистка чата;
- блокировка пользователя;
- подписка на канал;
- профиль пользователя;
- настройки;
- попытка realtime typing/presence;
- локальный WebRTC call UI и сигналинг foundation.

## Production target

В корне находятся:

- `prisma/schema.prisma` — целевая PostgreSQL схема;
- `docker-compose.yml` — PostgreSQL + Redis + MinIO;
- `.env.example` — production-oriented environment variables.

Текущий dev-server intentionally использует JSON persistence, чтобы приложение запускалось без скачивания npm-пакетов. Для production нужно подключить Prisma/PostgreSQL и S3/MinIO adapter, сохранив текущие API-контракты.

## Структура

```text
apps/
  api/
    server.js
    data/db.json
    uploads/
  web/
    index.html
    styles.css
    app.js
prisma/
  schema.prisma
docs/
infrastructure/docker/
tests/
scripts/
```

## Проверка

```bash
npm run typecheck
npm run lint
npm test
npm run build
```
