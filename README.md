# Gauge Learn

Documentation and course content for the [Gauge](https://withgauge.com) platform, built with [Mintlify](https://mintlify.com).

Covers Answer Engine Optimization (AEO) fundamentals and how to navigate the Gauge product — rankings & visibility, prompts & citations, Action Center, Ask Gauge, Reddit, ChatGPT Ads, and branded prompts.

## Running locally

Requires Node 19+.

```bash
npm i -g mintlify    # one-time install
mintlify dev         # starts dev server at http://localhost:3000
```

If dependencies get out of sync, run `mintlify install` from the project root.

## Structure

```
introduction/   Welcome, what is AEO, core AEO metrics
setup/          Integrations and settings
navigating/     Per-feature walkthroughs of the Gauge app
resources/      Glossary, FAQ, changelog
snippets/       Reusable MDX snippets
logo/           Light/dark logo assets
custom.css      Theme overrides
docs.json       Mintlify site config (navigation, theme, nav links)
mint.json       Legacy Mintlify config (kept for compatibility)
```

All content is authored in MDX. Update the `navigation` array in `docs.json` when adding new pages.

## Deploying

Pushes to `main` are deployed automatically by Mintlify once the repo is connected to a Mintlify project.
