# OpenClaw: установка правил

Правила для OpenClaw из **ElucidatingYourLLM** (14 правил: 11 основных + 3 по необходимости).



## Что здесь

- `agents-rules.md` — основные правила для вставки в `AGENTS.md` + блок-роутер read-on-demand
- `specific/` — правила, загружаемые агентом по описанию задачи (read on demand)

## Как это работает

Основные правила (m/c) встраиваются прямо в `AGENTS.md` и загружаются при каждом старте сессии.
Правила в `specific/` хранятся отдельно — агент читает нужный файл, когда задача соответствует условию из блока-роутера в `AGENTS.md`.

## Установка вручную

1. Вставьте содержимое `agents-rules.md` в ваш `~/.openclaw/workspace/AGENTS.md`.
2. Скопируйте папку `specific/` в `~/.openclaw/workspace/specific/`.
3. Запустите новую сессию OpenClaw.

Если в вашем `AGENTS.md` уже есть правила — проверьте на дублирование перед вставкой.

## Установка через AI

Дайте AI ссылку на файл воркфлоу:

```
Прочитай https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/openclaw/ru/deploy-workflow.md и установи правила.
```

AI прочитает ваш текущий `AGENTS.md`, выявит пересечения и предложит план интеграции.

## Состав правил

- `specific/file-editing.md`
- `specific/pre-install-check.md`
- `specific/structural-analogy.md`
