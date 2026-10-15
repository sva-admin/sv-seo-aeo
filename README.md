<p align="center"><a href="https://loop.sv-academy.org"><img src="https://raw.githubusercontent.com/sva-admin/claude-skills/main/assets/sv-academy-512.png" width="88" alt="Silicon Valley Academy"/></a></p>

# sv-seo-aeo

Get a new website found by Google, Bing and the AI engines in about 40 minutes. Claude writes the code, you press the buttons.

An original skill by Silicon Valley Academy.

## What it does

A site that is live is not a site that can be found. Two kinds of machine decide whether customers ever hear about you: search engines, and the AI assistants people now ask instead of searching. This skill makes your site readable to both, then walks you through telling them it exists.

| Phase | Who does it | What happens |
|---|---|---|
| 1. Machine readable | Claude | Title and description, social card, one JSON-LD facts block, `robots.txt` that lets the AI crawlers in by name, `sitemap.xml`, `llms.txt` |
| 2. Google Search Console | You, guided click by click | URL prefix property, HTML tag verification, Claude places the tag and deploys |
| 3. Sitemap and indexing | You | Submit `sitemap.xml`, request indexing for the home page |
| 4. Bing Webmaster Tools | You | One click import from Google. This is the index ChatGPT search and Copilot lean on |
| 5. IndexNow | Claude, then one link for you | Optional direct ping to Bing |
| 6. Prove it | Both | Rich Results Test, Schema validator, share preview, then a one week measure plan |

Three rules it will not break: it never invents a fact about your business, it never asks for a password, and it hides pages that hold customer data instead of promoting them.

Written for static sites, including static HTML served by Hono on SV Cloud. It adapts the same artifacts to other stacks.

## The visual guide

Every button in phases 2 to 4 is drawn out, in English and Thai, with prompts you can copy:

https://sv-academy.org/seoaeo

## Install

Paste this into Claude Code:

```
Install the sv-seo-aeo skill from github.com/sva-admin/sv-seo-aeo
```

Then, in the project of a site that is already live, type `/sv-seo-aeo`. It also triggers on "seo", "aeo", "get my site on Google", "submit to Bing", "search console", "make ChatGPT find my site", or right after a first deploy.

## What to expect

A brand new address takes from a few days to a few weeks to appear, and no tool can guarantee indexing. The skill ends with a simple daily check so you can see the day it happens.

## Learn free

Learn free at https://loop.sv-academy.org/tutorials

## License

MIT. See [LICENSE](LICENSE).

---

More skills: https://github.com/sva-admin/claude-skills
Silicon Valley Academy: https://sv-academy.org

SV Academy is the education brand of [Silicon Valley Innovation](https://svinnovation.com), a Bangkok software and AI company that can build this for your business.
