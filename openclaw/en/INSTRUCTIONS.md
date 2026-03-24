# OpenClaw: установка правил

Правила для OpenClaw из **ElucidatingYourLLM** (14 правил: 11 основных + 3 запускаемых по условию).



## Что здесь

- `agents-rules.md` — основные правила для вставки в `AGENTS.md` + блок-роутер read-on-demand
- `specific/` — специфические правила для конкретных задач, загружаемые агентом по описанию задачи (read on demand):
  - `file-editing.md`
  - `pre-install-check.md`
  - `structural-analogy.md`

## Как это работает

Основные правила (m/c) встраиваются прямо в `AGENTS.md` и загружаются при каждом старте сессии.
Правила в `specific/` хранятся отдельно — агент читает нужный файл, когда задача соответствует условию из блока-роутера в `AGENTS.md`.

## Установка через AI

Дайте AI ссылку на файл воркфлоу:

```
Прочитай https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/openclaw/ru/deploy-workflow.md и установи правила.
```

AI прочитает ваш текущий `AGENTS.md`, выявит пересечения и предложит план интеграции.

## Установка вручную

1. Вставьте содержимое `agents-rules.md` в ваш `~/.openclaw/workspace/AGENTS.md`.
2. Скопируйте папку `specific/` в `~/.openclaw/workspace/specific/`.
3. Запустите новую сессию OpenClaw.

Если в вашем `AGENTS.md` уже есть правила — проверьте на дублирование перед вставкой.
