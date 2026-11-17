# Upstream & attribution

- **Upstream repository:** https://github.com/tristan-mcinnis/pptx-from-layouts-skill
- **Author:** Tristan McInnis
- **License:** MIT (see LICENSE)
- **Forked on:** 2026-11-17

This repository is a fork of the upstream project, kept for personal Claude Code
use. All code, docs, schemas, templates and examples remain the work of the
original author.

## What the skill does

Generates PowerPoint decks from a markdown outline by reading your own `.pptx`
template's **slide master layouts** and filling real placeholders - rather than
duplicating decorative slides and overlaying text boxes.

Pipeline: `pptx-profile` (profile the template) -> `pptx-author` (write a tagged
outline) -> `pptx-from-layouts` (render and validate the deck).

## Install (Claude Code)

```bash
git clone https://github.com/Ryen-Xie/pptx-from-layouts-skill.git
mkdir -p ~/.claude/skills ~/.claude/agents
cp -r pptx-from-layouts-skill/.claude/skills/pptx-from-layouts ~/.claude/skills/
cp pptx-from-layouts-skill/.claude/agents/*.md ~/.claude/agents/
pip install python-pptx pydantic
```

## Quick use

```bash
# 1) profile your own template once
python ~/.claude/skills/pptx-from-layouts/scripts/profile.py \
  your-template.pptx --name your-template --generate-config \
  --output-dir ~/.claude/skills/pptx-from-layouts/templates/

# 2) generate a deck from an outline
python ~/.claude/skills/pptx-from-layouts/scripts/generate.py outline.md -o deck.pptx \
  --template your-template.pptx \
  --config ~/.claude/skills/pptx-from-layouts/templates/your-template-config.json --validate
```
