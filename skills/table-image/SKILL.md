---
name: table-image
description: Generate images from tables for better readability in messaging apps like Telegram. Use when displaying tabular data.
metadata: {"clawdis":{"emoji":"📊"}}
---

# Table Image Skill

Render markdown tables as PNG images for messaging platforms that don't support markdown tables.

## Usage

Use `tablesnap` CLI to convert markdown tables to PNG:

```bash
echo "| Header 1 | Header 2 |
|----------|----------|
| Data 1   | Data 2   |" | ~/repos/tablesnap/tablesnap -o /tmp/table.png
```

Then send with `MEDIA:/tmp/table.png`

## Options

```bash
~/repos/tablesnap/tablesnap [flags]

Flags:
  -i string        Input file (default: stdin)
  -o string        Output file (default: stdout)
  --theme string   Theme: dark or light (default "dark")
  --font-size int  Font size (default 14)
  --padding int    Cell padding (default 10)

Subcommands:
  emojis install   Download full Twemoji set (~14MB) for all emoji support
```

## Emoji Support

**Bundled** (work out of the box): ✅ ❌ 🔴 🟢 🟡 ⭕ ⚠️

**Full emoji** (after `tablesnap emojis install`): All 3,689 emoji work

**Unsupported emoji** render as □ (fallback)

## Example Workflow

```bash
# Create table image
echo "| Task | Status |
|------|--------|
| Build | ✅ |
| Deploy | 🚀 |" | ~/repos/tablesnap/tablesnap -o /tmp/table.png

# Send in reply
MEDIA:/tmp/table.png
```

## Text Symbols

The bundled Inter font also supports:

| Use | Symbol |
|-----|--------|
| Check | ✓ |
| Cross | ✗ |
| Bullet | ● ○ |
| Star | ★ ☆ |
| Arrow | → ← ↑ ↓ |

## Notes

- Dark theme by default (matches Telegram dark mode)
- Auto-sizes to fit content
- Output ~10-20KB (Telegram-friendly)
- Repo: https://github.com/joargp/tablesnap
