# Changelog

Все значимые изменения в канонической версии правил.

Формат: [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

---

## [2.0.0] — 2026-03-11

### Добавлено
- Двуязычная структура репозитория: папки `ru/` и `en/` с полным набором правил, воркфлоу и скиллов
- Инструкции по установке на двух языках: `INSTRUCTIONS.ru.md`, `INSTRUCTIONS.en.md`

### Удалено
- Корневые папки `rules/`, `workflows/`, `skills/` — устаревшие дубли, заменены структурой `ru/`

---

## [1.0.0] — 2026-03-10

### Добавлено
- Базовые правила: поведение AI, защита от ошибок, коммуникация (`rules/core.md`)
- Архитектура информации и качество контента (`rules/information-architecture.md`)
- Управление файлами и документами (`rules/file-management.md`)
- Управление скриптами (`rules/scripts-management.md`)
- Git-воркфлоу (`rules/git-workflow.md`)
- Доменные правила: python-proxy, video-editing, markdown-dates, excel-files, generated-docs, pre-install-check, settings-change-tracking, technical-documents
- Воркфлоу деплоя для Cursor, Claude Code, OpenClaw
- Скилл `deploy-elucidating-rules`
