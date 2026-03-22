*[Русский текст ниже — перейти сразу](#ru--что-это-такое)*

# ElucidatingYourLLM — Tame Your LLM, Don't Let It Tame You

> **Rules are just the beginning.** Deploying them is step one.  
> Using them well — learning to be a genuine Human-in-the-Loop — is the actual work.

**EN:** A battle-tested set of rules for AI assistants (Cursor, Claude Code, OpenClaw) — ready to deploy in minutes.

**RU:** Проверенный набор правил для AI-ассистентов (Cursor, Claude Code, OpenClaw) — готов к деплою за несколько минут.

---

## EN · What is this?

A battle-tested set of rules for AI assistants — ready to deploy. Comes with deployment guides for each platform.

**But rules alone won't make your AI work better.**  
The real leverage is in how *you* work with the rules: noticing what's off, correcting it, verifying corrections, and systematically expanding what your AI can do for you.

That's the Human-in-the-Loop (HITL) framework — and it's what separates people who get 10x value from AI from people who just get autocomplete.

### Structure

The repository is organized by platform, then by language:

```
cursor/
└── ru/
    ├── INSTRUCTIONS.md       ← read this first
    ├── deploy-workflow.md    ← for your AI to execute
    ├── .cursorrules
    └── .cursor/rules/*.mdc

claude-code/
└── ru/
    ├── INSTRUCTIONS.md
    ├── deploy-workflow.md
    ├── CLAUDE.md
    └── .claude/rules/*.md

openclaw/
└── ru/
    ├── INSTRUCTIONS.md
    ├── deploy-workflow.md
    ├── agents-rules.md
    └── specific/*.md
```

### How to deploy

**Option 1 — manual:**  
Copy the files from your platform folder to your project root.  
See `INSTRUCTIONS.md` in the platform folder for exact steps.

**Option 2 — via AI (recommended):**  
Give your AI a link to the `deploy-workflow.md` for your platform:

```
Cursor:      https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/cursor/ru/deploy-workflow.md
Claude Code: https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/claude-code/ru/deploy-workflow.md
OpenClaw:    https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/openclaw/ru/deploy-workflow.md
```

Your AI will read the rules, check for conflicts with your existing setup, and deploy everything.

### Context window impact

The rules are lightweight. At DEFAULT load (rules that are always active), they consume:

| Platform | Tokens | % of 200K context |
|----------|--------|-------------------|
| Cursor | ~4,350 | 2.2% |
| Claude Code | ~4,100 | 2.1% |
| OpenClaw | ~3,400 | 1.7% |

TOTAL (all rules including on-demand): 4,300–4,600 tokens per platform.  
EN versions are ~12–15% more compact than RU.

### Model compatibility

The ruleset was developed and tested primarily on **Claude Opus 4.6** and **Claude Sonnet 4.6**. These are the models the rules were written for — and where they perform at their best.

Other models may work well too, but may require additional tuning or supplementary rules to get the same level of compliance.

**On weaker or smaller models:** the rules still help, but not at full capacity. Smaller models were not the design target, and they have less ability to consistently follow a structured ruleset. That said, partial compliance is still better than no rules at all — even a weaker model behaves more predictably with rules than without them.

### Want more rules?

This repository contains the **Principal** rule set — the foundational rules that every AI user needs.

For the complete **Advanced** set (32 rules across all platforms, including specialized rules for scripts, Git, Excel, video, and more), see:  
→ [SharpHandsOnLLM](https://github.com/FrigateCaptain/SharpHandsOnLLM) *(access by subscription)*

---

## RU · Что это такое?

Проверенный набор правил для AI-ассистентов (Cursor, Claude Code, OpenClaw).  
Готов к деплою. Содержит пошаговые инструкции для каждой платформы.

**Правила — только начало.**  
Настоящий результат приходит от того, как ты работаешь с правилами: замечаешь отклонения, корректируешь, верифицируешь поправки, систематически расширяешь то, что AI умеет делать за тебя.

Это и есть фреймворк Human-in-the-Loop (HITL) — именно он отличает людей, которые получают кратный результат от AI, от тех, кто просто пользуется автодополнением.

### Структура

Репозиторий организован по платформам:

```
cursor/ru/        — правила для Cursor IDE
claude-code/ru/   — правила для Claude Code
openclaw/ru/      — правила для OpenClaw
```

В каждой папке — `INSTRUCTIONS.md` с инструкцией по деплою и `deploy-workflow.md` для автоматической установки через AI.

### Как задеплоить

**Вариант 1 — вручную:**  
Скопируйте файлы из папки вашей платформы в корень проекта.  
Подробности — в `INSTRUCTIONS.md` в папке платформы.

**Вариант 2 — через AI (рекомендую):**  
Дайте AI ссылку на `deploy-workflow.md` для вашей платформы:

```
Cursor:      https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/cursor/ru/deploy-workflow.md
Claude Code: https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/claude-code/ru/deploy-workflow.md
OpenClaw:    https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/openclaw/ru/deploy-workflow.md
```

AI прочитает правила, проверит конфликты с вашими текущими правилами и задеплоит всё самостоятельно.

### Нагрузка на контекстное окно

Правила лёгкие. При DEFAULT-загрузке (правила, которые активны всегда) они занимают:

| Платформа | Токенов | % от 200K контекста |
|-----------|---------|---------------------|
| Cursor | ~4 350 | 2,2% |
| Claude Code | ~4 100 | 2,1% |
| OpenClaw | ~3 400 | 1,7% |

TOTAL (все правила, включая загружаемые по необходимости): 4 300–4 600 токенов на платформу.  
EN-версии на ~12–15% компактнее RU.

### Совместимость с моделями

Основной корпус правил разрабатывался и тестировался на **Claude Opus 4.6** и **Claude Sonnet 4.6** — именно под эти модели они написаны и на них показывают максимальный результат.

Другие модели тоже работают, но могут потребовать дополнительной настройки или дополнительных правил для достижения того же уровня соблюдения.

**На слабых или маленьких моделях:** правила помогают, но не в полную силу. Маленькие модели не были целевой аудиторией при разработке, и они хуже справляются с последовательным следованием структурированному набору правил. При этом даже частичное соблюдение правил лучше, чем их полное отсутствие — с правилами даже слабая модель ведёт себя предсказуемее.

### Хочешь больше правил?

Этот репозиторий содержит **базовый (Principal)** набор — правила, которые нужны каждому пользователю AI.

Полный **расширенный (Advanced)** набор (32 правила на всех платформах, включая специализированные правила для скриптов, Git, Excel, видео и др.):  
→ [SharpHandsOnLLM](https://github.com/FrigateCaptain/SharpHandsOnLLM) *(доступ по подписке)*

---

*Создан: 21 марта 2026*  
*Актуализирован: 22 марта 2026*
