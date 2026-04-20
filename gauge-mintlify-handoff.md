# Gauge Learn — Mintlify Onboarding Center
## Claude Code Project Handoff

---

## Project Overview

Build a structured onboarding/help center for Gauge customers using Mintlify, hosted at `learn.withgauge.com`. The center is modeled as a video course (similar to Profound University) with written documentation alongside each lesson.

**Reference UI:** Profound University — left sidebar with grouped course sections, video player on the right, summary/transcript tabs below the video.

---

## Goals

- Give new customers a zero-to-expert course experience navigating the Gauge platform
- Serve as an ongoing reference for existing customers
- Be maintainable by the entire Gauge team via GitHub
- Launch by end of this week (EOW)

---

## Course Structure

There are 3 sections and 11 total lessons. Some videos are not yet filmed — use "Coming Soon" placeholder pages for those.

### Section 1: Introduction
1. Welcome to Gauge
2. What is AEO?
3. Core AEO Metrics

### Section 2: Setup
4. Integrations & Settings

### Section 3: Navigating Gauge
5. Rankings & Visibility
6. Prompts & Citations
7. Action Center / Content
8. Ask Gauge
9. Reddit
10. ChatGPT Ads
11. Branded Prompts

---

## Technical Spec

### Platform
- **Tool:** [Mintlify](https://mintlify.com)
- **Repo:** GitHub (team will contribute via PRs or direct edits)
- **Custom Domain:** `learn.withgauge.com`
- **Branding:** Use Mintlify defaults for now — colors/fonts will be customized later

### Video Hosting
- Videos are hosted on **YouTube**
- Embed using `<iframe>` with `16:9` aspect ratio
- YouTube thumbnail displays natively before play — no extra work needed
- For videos not yet filmed, show a styled "Coming Soon" placeholder instead of the iframe

### Page Template (per lesson)
Each of the 11 lesson pages should follow this structure:
1. **Video embed** (YouTube iframe, full width, 16:9, rounded corners) OR Coming Soon placeholder
2. **Summary section** — Key concepts from the lesson (bullet points)
3. **Written documentation** — Detailed written content supporting the video
4. **Callout blocks** — Use Mintlify's `<Note>`, `<Tip>`, or `<Warning>` components to highlight important actions
5. **"Next Lesson" button** — Footer nav linking to the next page in sequence

---

## File Structure to Build

```
/
├── mint.json                  # Main config — navigation, branding, domain
├── introduction/
│   ├── welcome.mdx
│   ├── what-is-aeo.mdx
│   └── core-aeo-metrics.mdx
├── setup/
│   └── integrations-and-settings.mdx
├── navigating/
│   ├── rankings-visibility.mdx
│   ├── prompts-citations.mdx
│   ├── action-center.mdx
│   ├── ask-gauge.mdx
│   ├── reddit.mdx
│   ├── chatgpt-ads.mdx
│   └── branded-prompts.mdx
├── resources/
│   ├── glossary.mdx           # AEO terms glossary
│   ├── faq.mdx                # Frequently asked questions
│   └── changelog.mdx          # Product updates
└── snippets/
    └── coming-soon.mdx        # Reusable Coming Soon component
```

---

## mint.json Configuration

```json
{
  "name": "Gauge Learn",
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg"
  },
  "favicon": "/favicon.svg",
  "colors": {
    "primary": "#0D9373",
    "light": "#07C983",
    "dark": "#0D9373"
  },
  "topbarLinks": [
    {
      "name": "Back to Gauge",
      "url": "https://app.withgauge.com"
    }
  ],
  "navigation": [
    {
      "group": "Introduction",
      "pages": [
        "introduction/welcome",
        "introduction/what-is-aeo",
        "introduction/core-aeo-metrics"
      ]
    },
    {
      "group": "Setup",
      "pages": [
        "setup/integrations-and-settings"
      ]
    },
    {
      "group": "Navigating Gauge",
      "pages": [
        "navigating/rankings-visibility",
        "navigating/prompts-citations",
        "navigating/action-center",
        "navigating/ask-gauge",
        "navigating/reddit",
        "navigating/chatgpt-ads",
        "navigating/branded-prompts"
      ]
    },
    {
      "group": "Resources",
      "pages": [
        "resources/glossary",
        "resources/faq",
        "resources/changelog"
      ]
    }
  ],
  "footerSocials": {
    "website": "https://withgauge.com"
  }
}
```

---

## MDX Page Templates

### Template A — Video Ready

```mdx
---
title: "Welcome to Gauge"
description: "Get oriented with the Gauge platform and understand what you'll learn in this course."
---

<iframe
  width="100%"
  style={{ aspectRatio: "16/9", borderRadius: "8px", border: "none" }}
  src="https://www.youtube.com/embed/YOUR_VIDEO_ID"
  title="Welcome to Gauge"
  allowFullScreen
/>

## Summary

<Note>
  This lesson covers what Gauge is, who it's for, and how to get the most out of this course.
</Note>

**Key Concepts:**
- What Gauge does and why AEO matters
- How to navigate this course
- What you'll be able to do after completing it

## Overview

[Written documentation goes here — expand on the video content, include screenshots, step-by-step instructions, etc.]

---

<Card title="Next Lesson →" icon="arrow-right" href="/introduction/what-is-aeo">
  What is AEO?
</Card>
```

### Template B — Coming Soon (video not yet filmed)

```mdx
---
title: "ChatGPT Ads"
description: "Learn how to track and optimize your brand's visibility in ChatGPT Ad placements."
---

<Warning>
  This lesson is coming soon. Check back shortly — we're finishing up the video for this module.
</Warning>

## What You'll Learn

- [Bullet point preview of what this lesson will cover]
- [Bullet point 2]
- [Bullet point 3]

## Overview

[Placeholder written documentation can go here in the meantime.]

---

<Card title="Next Lesson →" icon="arrow-right" href="/navigating/branded-prompts">
  Branded Prompts
</Card>
```

---

## Features To Implement

| Feature | Priority | Notes |
|---|---|---|
| YouTube video embeds with thumbnails | P0 | Native YouTube thumbnail shows before play |
| Sidebar course navigation | P0 | Configured via `mint.json` |
| Written docs per lesson | P0 | Alongside each video |
| Coming Soon placeholder pages | P0 | For unfilmed videos |
| "Next Lesson" footer buttons | P0 | Use Mintlify `<Card>` component |
| Custom domain `learn.withgauge.com` | P0 | DNS config after deploy |
| AEO Glossary page | P1 | Key terms defined |
| FAQ page | P1 | Common new customer questions |
| Changelog page | P1 | Mintlify has built-in support |
| Callout blocks (Note/Tip/Warning) | P1 | Highlight key actions per lesson |
| "Time to complete" per lesson | P2 | Add to page description metadata |
| Progress tracking | P3 | Not native to Mintlify — Phase 2 |

---

## What Claude Code Should Do

1. **Initialize the Mintlify project** — scaffold the full file/folder structure above
2. **Write `mint.json`** — full navigation config as specified
3. **Generate all 11 MDX lesson pages** — using the correct template (video ready vs. coming soon). Use placeholder YouTube video IDs where needed (format: `https://www.youtube.com/embed/PLACEHOLDER_ID`)
4. **Generate the 3 resource pages** — Glossary (with common AEO terms), FAQ, and Changelog
5. **Create the reusable Coming Soon snippet**
6. **Ensure each page has** — iframe or placeholder, summary, written doc section, callout block, and next lesson card
7. **Validate `mint.json`** — make sure all page paths resolve to actual files

---

## Additional Context

- **Platform being documented:** Gauge — an AEO (Answer Engine Optimization) platform that tracks brand visibility in AI-generated answers (ChatGPT, Perplexity, Gemini, etc.)
- **AEO** stands for Answer Engine Optimization — the practice of optimizing brand presence in AI search results, as opposed to traditional SEO
- **Key Gauge features:** Rankings & Visibility tracking, Prompt monitoring, Citation tracking, Reddit monitoring, ChatGPT Ads tracking, Branded Prompts, Ask Gauge (AI assistant), Action Center for content recommendations
- **Target users:** Marketing teams and brand managers who want to understand and improve their AI search presence

---

## Mintlify Setup Commands (run in project root)

```bash
# Install Mintlify CLI
npm i -g mintlify

# Start local dev server
mintlify dev

# The dev server runs at http://localhost:3000
```

---

## DNS Setup (for learn.withgauge.com)

Once the Mintlify project is deployed:
1. Go to Mintlify dashboard → Settings → Custom Domain
2. Add `learn.withgauge.com`
3. Mintlify will give you a CNAME record to add in your DNS provider
4. Add the CNAME, wait for propagation (~10 min)

---

## Notes for Claude Code

- Keep all written documentation sections as clear placeholders with `[bracketed instructions]` so the team knows exactly what to fill in
- Use consistent formatting across all 11 lesson pages
- The glossary should include at minimum: AEO, Answer Engine, Citation, Prompt, Visibility, Rankings, Branded Prompt, Action Engine
- Do not invent specific video IDs — use `PLACEHOLDER_VIDEO_ID` and note which videos still need their YouTube URL added
- If Mintlify's component syntax changes, refer to https://mintlify.com/docs for the latest `<Card>`, `<Note>`, `<Tip>`, `<Warning>` usage
