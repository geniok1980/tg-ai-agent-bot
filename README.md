# tg-ai-agent-bot

Telegram-бот на aiogram 3.x: webhook-приём обновлений, PostgreSQL с миграциями,
Redis для состояний, локализация (Fluent, ru/en), Docker Compose для dev и prod.

## Технологии

- **aiogram 3.x** — Telegram Bot API
- **FastAPI** — webhook-эндпоинт
- **PostgreSQL + Tortoise ORM** (миграции — Aerich)
- **Redis** — FSM-состояния и кэш
- **aiogram-i18n + Fluent** — локализация
- **Docker Compose** — окружения dev и prod

## Быстрый старт

```bash
cp .env.example .env    # токен бота, вебхук, доступы к БД и Redis
make dev                # или: make prod
```

Полезные команды:

```bash
make logs [service]     # логи
make ps                 # состояние контейнеров
make aerich migrate     # миграция после правки моделей
make aerich upgrade     # применить миграции
make db-backup          # резервная копия базы
```

Бот работает только через webhook — нужен публичный HTTPS-адрес.

## Структура

```
bot/
├── main.py          # FastAPI, настройка вебхука, жизненный цикл
├── core/            # конфигурация, загрузчик, логирование
├── handlers/        # обработчики: private, groups, ошибки
├── filters/         # фильтры (приватный чат, админ и т. д.)
├── keyboards/       # клавиатуры
├── middlewares/     # регистрация пользователей, i18n
├── models/          # модели Tortoise ORM
├── services/        # бизнес-логика
├── managers/        # БД, Redis, локали
├── locales/         # переводы Fluent (ru, en)
└── utils/           # вспомогательные утилиты
```

## Контакты

Telegram: [@geniok](https://t.me/geniok)

## Лицензия

MIT — см. [LICENSE](LICENSE).
