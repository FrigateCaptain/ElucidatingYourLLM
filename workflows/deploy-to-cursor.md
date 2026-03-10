# Деплой в Cursor

Пошаговая инструкция по деплою правил из этого репозитория в Cursor.

---

## Шаг 1. Ответьте на вопросы по настройке

### 1.1 Базовые правила

Базовые правила (`rules/core.md`, `rules/information-architecture.md`, `rules/file-management.md`, `rules/scripts-management.md`, `rules/git-workflow.md`) — рекомендуется включить все.

**Вопрос:** Хотите ли вы использовать раздел «Scripts Management» полностью? Он включает обязательный цикл: spec-файл → шапка → реестр при каждом создании скрипта. Если вы не пишете скрипты регулярно — можно оставить упрощённую версию.

### 1.2 Доменные правила

Посмотрите папку `rules/domain/`. Для каждого файла решите: включать или нет.

| Файл | Когда нужен |
|------|-------------|
| `python-proxy.md` | Используете Python и прокси/VPN |
| `pre-install-check.md` | Устанавливаете ПО через AI (рекомендуется всем) |
| `markdown-dates.md` | Ведёте документацию в markdown |
| `excel-files.md` | Работаете с Excel через Python |
| `generated-docs.md` | Создаёте DOCX/ODT программно |
| `video-editing.md` | Редактируете видео через ffmpeg |
| `technical-documents.md` | Ведёте техническую документацию в `technical/` |

### 1.3 Язык правил

Правила написаны на русском. Если вам нужны правила на другом языке — адаптируйте содержимое файлов.

### 1.4 Структура хранения правил

Два варианта организации правил в Cursor:

**Вариант А — монолитный** (всё в одном файле):
- Всё содержимое → один файл `.cursorrules` в корне workspace
- Проще, но правила загружаются в каждый разговор

**Вариант Б — модульный** (рекомендуется):
- Базовые правила → `.cursorrules`
- Доменные правила → `.cursor/rules/*.mdc` с соответствующими globs
- Правила загружаются только при работе с релевантными файлами

---

## Шаг 2. Создайте структуру папок

```bash
mkdir -p .cursor/rules
```

---

## Шаг 3. Разместите базовые правила

Создайте `.cursorrules` в корне workspace. Скопируйте в него содержимое нужных файлов из `rules/`:
- `rules/core.md`
- `rules/information-architecture.md`
- `rules/file-management.md`
- `rules/scripts-management.md` (если нужен)
- `rules/git-workflow.md`

---

## Шаг 4. Разместите доменные правила

Для каждого выбранного файла из `rules/domain/` — создайте соответствующий `.mdc` в `.cursor/rules/`:

```
rules/domain/python-proxy.md        → .cursor/rules/python-proxy.mdc
rules/domain/pre-install-check.md   → .cursor/rules/pre-install-check.mdc
rules/domain/markdown-dates.md      → .cursor/rules/markdown-dates.mdc
...
```

В начало каждого `.mdc` добавьте YAML frontmatter:

```yaml
---
description: "Краткое описание правила"
globs: "**/*.py"       # паттерн файлов (см. таблицу ниже)
alwaysApply: false
---
```

Рекомендуемые globs:

| Правило | globs | alwaysApply |
|---------|-------|-------------|
| python-proxy | `**/*.py` | false |
| pre-install-check | — | true |
| markdown-dates | `**/*.md` | false |
| excel-files | `**/*.xlsx, **/*.xls` | false |
| generated-docs | `**/*.docx, **/*.odt` | false |
| video-editing | `**/*.mp4, **/*.mkv, **/*.avi, **/*.webm, **/*.mov` | false |
| technical-documents | `**/technical/**/*.md` | false |

---

## Шаг 5. Проверьте работоспособность

1. Откройте Cursor в папке workspace
2. Начните новый разговор
3. Спросите: «Какие правила у тебя есть?» или «Прочитай .cursorrules»
4. Убедитесь, что AI видит правила

Для доменных правил: откройте файл с соответствующим расширением (например `.py`) и проверьте, что AI ссылается на правила из `.mdc`.

---

## Шаг 6. Персонализация

После проверки — адаптируйте под себя:
- Измените языковую политику
- Добавьте или уберите разделы
- Добавьте специфичные для вашего проекта правила

---

## Обновление

При выходе новой версии правил:
1. `git pull` в папке ElucidatingYourLLM
2. Сравнить CHANGELOG.md — что изменилось
3. Перенести нужные изменения в свои `.cursorrules` и `.mdc`
