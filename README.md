# ElucidatingYourLLM — Tame Your LLM, Don't Let It Tame You

> **Rules are just the beginning.** Deploying them is step one.  
> Using them well — learning to be a genuine Human-in-the-Loop — is the actual work.

---

## EN · What is this?

A battle-tested set of rules, workflows, and skills for AI assistants (Cursor, Claude Code, OpenClaw).  
Ready to deploy. Comes with deployment guides for each platform.

**But rules alone won't make your AI work better.**  
The real leverage is in how *you* work with the rules: noticing what's off, correcting it, verifying corrections, and systematically expanding what your AI can do for you.

That's the Human-in-the-Loop (HITL) framework — and it's what separates people who get 10x value from AI from people who just get autocomplete.

### Who this is for

**Group 1 — General AI users** (anyone using AI assistants day-to-day):

| Segment | What you get |
|---------|-------------|
| Just starting out | A solid foundation — rules, structure, deployment guide. Skip the months of trial-and-error. |
| Already using AI actively | Upgrade your setup immediately. Then learn the framework to move faster and get better results. |
| Power users | Deploy this to your colleagues, employees, partners. Better onboarding, faster ramp-up. |

**Group 2 — Managers, founders, executives** (using AI for business and leadership):

| Segment | What you get |
|---------|-------------|
| Just starting out | The right mental model from day one — AI as a managed resource, not a magic box. |
| Already using AI | A system that makes your AI investment compound over time, not plateau. |
| Advanced users | A framework for rolling out AI across your team and organization with consistency. |

---

## RU · Что это такое

Проверенный в реальной работе набор правил, воркфлоу и скиллов для AI-ассистентов (Cursor, Claude Code, OpenClaw).  
Готов к деплою. Инструкции по установке — для каждой платформы.

**Но правила сами по себе не решают задачу.**  
Главная работа — это умение с ними работать: замечать что идёт не так, корректировать, проверять корректировки, и систематически расширять то, что ваш AI умеет делать для вас.

Это и есть фреймворк Human-in-the-Loop (HITL, «человек в петле обратной связи»). Именно это отличает тех, кто получает от AI кратный результат, от тех, кто получает умный автокомплит.

---

## Learn the framework / Освоить фреймворк

Правила — это стартовая точка. Фреймворк — это то, как двигаться дальше.

### Для руководителей и предпринимателей (приоритет)

**Как смотреть на LLM глазами управленца** — курс о том, как встроить AI в управленческую работу так, чтобы он улучшал бизнес, предпринимательскую активность и решения.

📺 **Ознакомительное видео:** [[PLACEHOLDER: YouTube URL]]  
🎓 **Курс:** [[PLACEHOLDER: курс — ссылка]]

### Для всех, кто работает с AI

**Как обуздать LLM и онбордить её в свой мир** — курс о том, как смотреть на LLM через правильную оптику, чтобы она адаптировалась под вас, а не вы под неё.

📺 **Ознакомительное видео:** [[PLACEHOLDER: YouTube URL]]  
🎓 **Курс:** [[PLACEHOLDER: курс — ссылка]]

---

## Quick start / Быстрый старт

1. Выбрать платформу: [Cursor](workflows/deploy-to-cursor.md) · [Claude Code](workflows/deploy-to-claude-code.md) · [OpenClaw](workflows/deploy-to-openclaw.md)
2. Следовать воркфлоу — он задаст вопросы по настройке под ваш контекст
3. Или запустить скилл `deploy-elucidating-rules` прямо в Cursor/Claude Code

## Repository structure / Структура репозитория

```
rules/
├── core.md                     # AI behaviour, error protection, communication
├── information-architecture.md # Information architecture, content quality
├── file-management.md          # File and document management
├── scripts-management.md       # Script lifecycle management
├── git-workflow.md             # Git rules
└── domain/                     # Optional domain rules
    ├── python-proxy.md         # Python + proxy/VPN
    ├── video-editing.md        # ffmpeg workflows
    ├── markdown-dates.md       # Date tracking in docs
    ├── excel-files.md          # Excel via openpyxl
    ├── generated-docs.md       # DOCX/ODT generation
    ├── pre-install-check.md    # Compatibility before install
    └── technical-documents.md  # technical/ folder standards

workflows/
├── deploy-to-cursor.md         # Deploy to Cursor
├── deploy-to-claude-code.md    # Deploy to Claude Code
└── deploy-to-openclaw.md       # Deploy to OpenClaw

skills/
└── deploy-elucidating-rules/
    └── SKILL.md                # Interactive deployment skill
```

---

*Created: 10 March 2026*  
*Updated: 10 March 2026*
