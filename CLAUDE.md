# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## כללי עבודה (גלעד, 24.10.2026)

1. **מודלים:** התכנון נעשה ב-Opus 5.5 (`claude-opus-5-5`), והביצוע (כתיבת הקוד) ב-Sonnet 5.5
   (`claude-sonnet-5-5`), דרך סוכן משנה עם `model: "sonnet"`.
2. **ענפים:** עובדים ב-`dev`, ומעבירים ל-`main` רק קוד שנבדק.
3. **בסוף כל שינוי קוד, בסדר הזה:**
   1. בדיקות לקוד החדש.
   2. בדיקות רגרסיה: מריצים שוב את הבדיקה שבסעיף "Checking the site", על העמוד כולו.
   3. בדיקת אבטחה עם הכישור `security-review`. מתקנים את מה שנמצא ומדווחים לגלעד.
   4. commit, ואז push.
4. **תיעוד:** בסוף העבודה מתעדים באובסידאן כל עדכון, בפתק
   `פרויקטים/אתר תדמית מפתחי AI/אתר תדמית מפתחי AI.md`, ביומן העדכונים.
   הכספת היא התיקייה שמעל המאגר (`AI Course`). כותבים לפתק דרך `mcp__obsidian__*`.

## What this is

A one-page Hebrew (RTL) promo site for an AI developers group at the Hebrew University. `index.html` is the whole site: static HTML with inline CSS and one inline script for the AI-agent effects (hero network canvas, "live agents" console, stats count-up). The script writes to the DOM only via `textContent`/`createElement`, and respects `prefers-reduced-motion`. Fonts load from Google Fonts. All content is placeholder.

Public repo: https://github.com/gilad1979/huji-ai-site (account `gilad1979`, set in local git config).

## Checking the site

`file://` URLs rendered blank in `playwright-cli` because of the space in the parent folder name. Serve the folder instead:

```bash
python -m http.server 8765
playwright-cli open http://localhost:8765/   # then: screenshot, resize 390 844, console, close
```

The page should show no console errors (the missing `favicon.ico` 404 is expected) and no horizontal scroll at 390px: `document.documentElement.scrollWidth > innerWidth` should be `false`. Stop the server afterwards.

## Before publishing

The site uses the Hebrew University's name and mentions Hadassah. Don't publish it as a live site (including as a claude.ai Artifact) until the placeholder content and the email `ai-lab@example.ac.il` are replaced and the university has approved use of its name.
