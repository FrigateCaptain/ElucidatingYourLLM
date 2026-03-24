# Claude Code: установка правил

Правила для Claude Code из **ElucidatingYourLLM** (14 правил: 11 основных + 3 запускаемых по условию).



## Что здесь

- `CLAUDE.md` — основные правила (загружаются автоматически при каждой сессии)
- `.claude/rules/*.md` — специфические правила для конкретных задач (загружаются автоматически по условию: glob-паттерну файлов или всегда, если glob не задан)

## Установка через AI

Дайте AI ссылку на файл воркфлоу:

```
Прочитай https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/claude-code/ru/deploy-workflow.md и установи правила.
```

AI проверит конфликты с вашим текущим `CLAUDE.md`, предложит бэкап и выполнит установку.

## Установка вручную

1. Скопируйте `CLAUDE.md` в корень вашего проекта.
2. Скопируйте папку `.claude/` в корень вашего проекта.
3. Запустите новую сессию Claude Code.

Если в вашем проекте уже есть `CLAUDE.md` — сделайте бэкап перед копированием.

## Состав правил

- `.claude/rules/file-editing.md`
- `.claude/rules/pre-install-check.md`
- `.claude/rules/structural-analogy.md`
