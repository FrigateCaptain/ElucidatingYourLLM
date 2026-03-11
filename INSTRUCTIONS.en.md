# Installation Guide

*Created: 10 March 2026*  
*Updated: 10 March 2026*

---

## What this is and why it matters

This repository contains a set of rules, workflows, and skills for AI assistants
(Cursor, Claude Code, OpenClaw). The rules structure AI behavior — making it more
specific, attentive, and clear, while also reducing collisions, hallucinations, and
unexpected reactions — ultimately turning it into a sensible, reliable assistant.

The `ru/` folder contains rules in Russian.  
The `en/` folder contains the same rules in English.

---

## Step 1. Choose your platform

- [Cursor](en/workflows/deploy-to-cursor.md)
- [Claude Code](en/workflows/deploy-to-claude-code.md)
- [OpenClaw](en/workflows/deploy-to-openclaw.md)

> **Important:** use a more capable (larger) language model version for the
> installation — stronger models follow workflow instructions more accurately
> and make fewer mistakes during deployment.

---

## Step 2. Give your AI access to the repository

**Option A** — copy the `en/` folder to your local disk.  
**Option B** — give your AI a link to the `en/` folder on GitHub.

---

## Step 3. Run the deployment workflow

In your AI chat, point it to the relevant workflow (from step 1) and ask:

> "Here's the deployment workflow: [path or link]. Read it and deploy the rules
> into my system."

The AI will ask you setup questions, then:

1. Generate a version of the rules in your platform's format.
2. Check for overlaps and conflicts with your existing rules.
3. Show all discrepancies with an explanation of what changes.
4. Offer to create a backup before applying.
5. Apply the rules after your confirmation.

---

## Step 4. Learn the framework — and keep improving

The installed rules are a solid starting point, not the finish line.

Real results come from knowing how to keep working with them: spotting what's off,
fixing it, verifying, expanding. The deeper you understand how to work with AI and
how to adapt it to your needs — the more precisely you can tune it, the less time
you spend fixing mistakes, and the more confident you stay when tools change (and
they change every six months to a year).

To get there fast and with the right perspective:

- **For managers and founders:** "LLM in the Hands of a Manager: How to Strengthen
  Your Business and Optimize Management" — [PLACEHOLDER: link]
- **For everyone working with AI:** "How to Tame Your LLM and Onboard It into
  Your World" — [PLACEHOLDER: link]
- **Introductory video:** [Watch on YouTube](https://www.youtube.com/watch?v=8H31ofgYSdQ)
  ⚠️ *temporary video, will be replaced*

---

## If something goes wrong

If you run into collisions or unexpected AI behavior after installation:

1. Ask your AI to check for conflicts between the installed rules and your
   existing ones — it knows how to do this.
2. If you need to roll back — use the backup your AI created in step 3.

**Want to dig deeper on your own?** — the course gives you all the tools you need.

**Want to share a case?** — send a description with screenshots:
[PLACEHOLDER: contact]. We'll take a look.

---

## Beginner or advanced?

**Beginner:** just use the rules as your starting point — they come with sensible
defaults out of the box. Run the workflow, answer the AI's questions, get a working
configuration.

**Advanced:** run the workflow, review the discrepancies — and cherry-pick what
looks valuable. You don't have to adopt everything.
