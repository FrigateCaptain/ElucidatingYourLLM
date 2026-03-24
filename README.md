*[Русский текст ниже — перейти сразу](#ru--что-это-такое)*

# ElucidatingYourLLM — Tame Your LLM, Don't Let It Tame You

> **Rules are just the beginning.** Deploying them is step one.  
> Using them well — learning to be a genuine Human-in-the-Loop — is the actual work.

**EN:** A battle-tested **set of main and core rules** for your AI assistants (Cursor, Claude Code, OpenClaw) — ready to deploy in minutes.

**RU:** Проверенный **набор ключевых правил** для ваших AI-ассистентов (Cursor, Claude Code, OpenClaw) — готов к деплою за несколько минут.
*[→ Перейти к полному описанию на русском](#ru--что-это-такое)*

---

## EN · What is this?

A battle-tested **set of main and core rules** for your AI assistants — ready to deploy. Comes with step-by-step AI-assisted deployment guides for each platform.

> **This repo has the Principal rules. There's also an [Advanced set (18 extra rules)](#want-more-rules) and [courses](#courses) — details below.**

**But rules are just the beginning.**  
The real results come from ongoing work with the rules: how you notice deviations, correct them through new rules, verify the fixes, and systematically expand what your AI can do for you.

That's the **AI-Lucidability Framework** — what makes the Human-in-the-Loop (HITL) approach actually work. It's what separates people who get 10x value from AI from those who simply augment their usual workflow. [→ Courses](#courses)

### What you get

Your AI assistant becomes sensible, sharp, specific, and reliable — not only helping with day-to-day tasks but also continuously tuning and improving itself.

This includes both personal refinements and work by the "Key to Real Management" educational center, as well as community consensus standards as of March 2026. Fewer collisions, hallucinations, and unexpected behaviors. More predictability and more satisfaction from working with AI. Your AI stops acting like the "Two from the Chest":

![Two from the Chest — EN](assets/vovka-two-from-chest-en.gif)

Deploying the rules is step one. Step two is learning how to work with AI and how to adapt it for yourself so you can keep improving the system on your own: spot what's off, fix it, expand what's possible. That's what the [courses](#courses) are for — they give you the right lens and frameworks that hold up even when the tools change — and they will, within six months to a year. You'll be able to clearly understand which new tools fit your needs, what they're good for, and how to use them best.

### Want more rules?

Beyond this repository with the **Principal** rule set (the foundational rules every AI user needs), there is also the **Advanced** rule set — → [SharpHandsOnLLM](https://github.com/FrigateCaptain/SharpHandsOnLLM) — a supplement to ElucidatingYourLLM.  
It includes all Principal rules + 18 additional specialized rules, in particular:

- Rules management (how to structure your work with AI rule files so it stays a clear, productive tool)
- Projects management min (structuring and documenting project information so it's both human-readable (easy to recall what was done and why) and AI-readable (so the AI understands the logic and makes better suggestions))
- Backlogs management (how to organize work so nothing important-but-not-urgent falls through the cracks)
- Incident documentation (AI incident tracking — so the data a) accumulates and b) provides quality material for future analysis)
- Scripts management (rules and checklist for systematic, transparent script work — so your script collection doesn't turn into spaghetti as it grows)
- Excel files (openpyxl workflow)
- Generated documents (DOCX/ODT generation)
- Source attribution markers (visual cues that make trustworthiness immediately apparent)
- Skills/plugins safety
- Settings change tracking (so that if something breaks, you can figure out what was configured, how, and why)
- Technical documents formatting (readable structure)

Access is available to all who complete our courses or by subscription — [leave a request](#courses).

### Courses

- **For managers and founders:** "LLM in the Hands of a Manager: How to Strengthen Your Business and Optimize Management"
- **For everyone working with AI:** "How to Tame Your LLM and Onboard It into Your World"

Course graduates also get access to [advanced materials](https://github.com/FrigateCaptain/SharpHandsOnLLM).

Leave your contact if you're interested in courses or access to the advanced ruleset:

- 💬 **Telegram:** [@vitaly_zhandarov](https://t.me/vitaly_zhandarov) — write directly
- 📋 **[Interest form](https://forms.gle/p4iuK5CF32b199AH9)** — Google Form (1 min)
- 🐙 **[GitHub Issue](../../issues/new?template=interest.md)** — if you prefer GitHub

*Всё это также доступно [на русском языке ниже](#хочешь-больше-правил).*

### Who this is for

**General AI users** (anyone using their AI assistants day-to-day):
- Just starting out — a solid foundation: rules, structure, deployment guide. Skip the months of trial-and-error.
- Already using AI actively — immediate upgrade; leverage to move faster.

**Managers, founders, executives:**
- Just starting out — the right mental model from day one: AI as a managed resource, not a magic box.
- Already using AI — a system that makes your AI investment compound over time, not plateau.
- Advanced users — a framework for rolling out AI across your team and organization with consistency.

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

**Option 1 — via AI (recommended):**  
Give your AI a link to the `deploy-workflow.md` for your platform:

```
Cursor:      https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/cursor/ru/deploy-workflow.md
Claude Code: https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/claude-code/ru/deploy-workflow.md
OpenClaw:    https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/openclaw/ru/deploy-workflow.md
```

Your AI will read the rules, check for conflicts with your existing setup, and deploy everything.

**Option 2 — manual:**  
Copy the files from your platform folder to your project root.  
See `INSTRUCTIONS.md` in the platform folder for exact steps.

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

**When extending or adding new rules with AI:** it is critically important to use the most capable model available (e.g., Opus 4.6). Rule quality and consistency across the ruleset depend on the model's ability to reason about complex behavioral constraints — weaker models produce lower-quality rules that may conflict with or undermine existing ones, or simply fail to produce the intended effect.

---

## RU · Что это такое?

Проверенный **набор ключевых правил** для ваших AI-ассистентов (Cursor, Claude Code, OpenClaw).  
Готов к деплою. Содержит пошаговые инструкции для развёртывания с помощью ИИ для каждой платформы.

> **Здесь — базовый (Principal) набор правил. Есть также [расширенный набор (18 доп. правил)](#хочешь-больше-правил) и [курсы](#курсы) — подробности ниже.**

**Правила — только начало.**  
Настоящий результат получается от дальнейшей работы с правилами: как ты замечаешь отклонения, корректируешь через новые правила, верифицируешь поправки и систематически расширяешь то, что AI умеет делать за тебя.

Это и есть **фреймворк AI-Lucidability** (ИИ-контрастирования), делающий подход Human-in-the-Loop (HITL) по-настоящему рабочим — именно AI-Lucidability отличает людей, которые получают кратный результат от AI, от тех, кто просто дополняет привычные действия. [→ Курсы](#курсы)

### Что вы получаете

Ваш AI-ассистент становится адекватным, толковым, конкретным и исполнительным — и не только помогает в повседневных задачах, но и последовательно настраивает и улучшает себя.

Здесь воплощены как личные наработки, так и наработки нашего учебно-методического центра «Ключ к реальному управлению», а также учтены консенсусные стандарты сообществ по состоянию на март 2026 года. Меньше коллизий, галлюцинаций, неожиданных реакций. Больше предсказуемости и удовольствия от работы. AI перестаёт делать «как двое из ларца»:

![Двое из ларца — RU](assets/vovka-two-from-chest-ru.gif)

Установка правил — это шаг первый. Шаг второй — освоить логику работы с AI, логику его адаптации под себя, чтобы продолжать улучшать систему самостоятельно: замечать что идёт не так, корректировать, расширять возможности. Для этого приходите к нам на [курсы](#курсы) — они дают правильную оптику и фреймворки, которые работают. И даже когда инструменты изменятся — а через полгода-год они изменятся точно — вы сможете ясно понимать, что из новых инструментов подходит, для чего и как их лучше использовать.

### Хочешь больше правил?

Кроме текущего репозитория с **базовым (Principal)** набором правил, которые нужны каждому пользователю AI, есть ещё **Расширенный (Advanced)** набор правил — → [SharpHandsOnLLM](https://github.com/FrigateCaptain/SharpHandsOnLLM) — дополнение к ElucidatingYourLLM.  
Он включает все базовые правила + 18 специализированных, в частности:

- Управление правилами (как построить работу с файлами правил AI, чтобы это было ясным и продуктивным инструментом)
- Управление проектами min (структурирование и фиксация информации о проекте таким образом, чтобы она была и хорошо человекочитаемой (легко вспомнить, что и зачем делалось) и ИИ-читаемой (чтобы ИИ адекватнее понимал логику и делал/предлагал адекватные решения))
- Управление бэклогами (как организовать работу, чтобы всё нужное но не срочное не терялось)
- Документирование инцидентов (отслеживание AI-инцидентов, чтобы информация а) накапливалась б) давала впоследствии качественные данные)
- Управление скриптами (правила и чеклист, обеспечивающие упорядоченную системную работу со скриптами, чтобы всё было прозрачно, а набор скриптов при разрастании не превращался в спагетти-код)
- Excel-файлы (воркфлоу openpyxl)
- Генерируемые документы (создание DOCX/ODT)
- Маркеры источников (визуализация, чтобы достоверность была наглядной)
- Безопасность скиллов/плагинов
- Фиксация изменений настроек (чтобы если что-то перестанет работать — можно было разобраться, что и как настроено или должно быть настроено, и почему именно так)
- Форматирование технических документов (удобочитаемая структура)

Доступ к нему выдаётся всем, прошедшим наши курсы, или по подписке — [оставляйте заявки](#курсы).

### Курсы

- **Для руководителей и предпринимателей:** «LLM в руках управленца: как усилить бизнес и оптимизировать управление»
- **Для всех, кто работает с AI:** «Как обуздать LLM и онбордить её в свой мир»

Прошедшие курс также получают доступ к [расширенным материалам](https://github.com/FrigateCaptain/SharpHandsOnLLM).

Оставить заявку, если интересны курсы или доступ к расширенному набору правил:

- 💬 **Telegram:** [@vitaly_zhandarov](https://t.me/vitaly_zhandarov) — пишите напрямую
- 📋 **[Форма заявки](https://forms.gle/p4iuK5CF32b199AH9)** — Google Form (1 минута)
- 🐙 **[GitHub Issue](../../issues/new?template=interest.md)** — если удобнее через GitHub

### Для кого это

**Все, кто работает с AI** (используют AI-ассистентов в повседневной работе):
- Только начинаете — фундамент: правила, структура, инструкция по установке. Пропускаете месяцы проб и ошибок.
- Активно используете — мгновенное улучшение; подспорье, чтобы двигаться быстрее.

**Руководители, предприниматели, управленцы:**
- Только начинаете — правильная модель с первого дня: AI как управляемый ресурс, а не магическая коробка.
- Уже используете — система, которая наращивает отдачу от AI со временем, а не выходит на плато.
- Продвинутые пользователи — фреймворк для масштабирования AI на команду и организацию с единым стандартом.

### Структура

Репозиторий организован по платформам:

```
cursor/ru/        — правила для Cursor IDE
claude-code/ru/   — правила для Claude Code
openclaw/ru/      — правила для OpenClaw
```

В каждой папке — `INSTRUCTIONS.md` с инструкцией по деплою и `deploy-workflow.md` для автоматической установки через AI.

### Как задеплоить

**Вариант 1 — через AI (рекомендую):**  
Дайте AI ссылку на `deploy-workflow.md` для вашей платформы:

```
Cursor:      https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/cursor/ru/deploy-workflow.md
Claude Code: https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/claude-code/ru/deploy-workflow.md
OpenClaw:    https://github.com/FrigateCaptain/ElucidatingYourLLM/blob/main/openclaw/ru/deploy-workflow.md
```

AI прочитает правила, проверит конфликты с вашими текущими правилами и задеплоит всё самостоятельно.

**Вариант 2 — вручную:**  
Скопируйте файлы из папки вашей платформы в корень проекта.  
Подробности — в `INSTRUCTIONS.md` в папке платформы.

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

**При доработке и добавлении новых правил с помощью ИИ:** критически важно использовать наиболее старшую из доступных моделей (например, Opus 4.6). Качество правил и их согласованность с уже существующими зависят от способности модели рассуждать о сложных поведенческих ограничениях — более слабые модели генерируют правила худшего качества, которые могут конфликтовать с уже имеющимися или подрывать их действие, или даже просто не давать нужный эффект.

---

*Создан: 21 марта 2026*  
*Актуализирован: 25 марта 2026, 00:15*
