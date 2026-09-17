---
name: sv-seo-aeo
description: Get a newly deployed website found by Google, Bing and the AI engines (ChatGPT, Claude, Perplexity, Copilot, Gemini) in about 40 minutes. Adds metadata, social cards, JSON-LD, robots.txt with an AI crawler allowlist, sitemap.xml and llms.txt to a static or Hono site, then walks the owner click by click through Google Search Console, Bing Webmaster Tools and IndexNow, and checks the result. Trigger on "/sv-seo-aeo", "seo", "aeo", "get my site on Google", "submit to Bing", "search console", "make ChatGPT find my site", "llms.txt", or right after a first deploy of a landing page.
---

# SV SEO + AEO

## Objective

Take a site that is live but invisible and make it readable to the two kinds of machine that send customers: search engines, and the AI assistants people now ask instead of searching. You write the code. The owner presses the buttons in their own Google and Bing accounts, because only they can. Finish with proof, not with a claim.

The owner is usually a business owner, not an engineer. Speak plainly, in the language they write to you in. One step at a time. Never show them a wall of instructions.

Companion page with drawn screens for every button below: https://sv-academy.org/seoaeo

## Hard rules

1. **Never invent a fact.** Every word in metadata, JSON-LD and llms.txt must already be on the page or come from the owner in this conversation. No review counts, no "since 1995", no awards, no opening hours, no address they did not give you. A missing fact means the field is left out and goes on the "Missing facts" list at the end. One wrong fact teaches an AI engine to distrust the rest.
2. **JSON-LD text matches the visible page word for word.** Validators flag a mismatch, and so do people.
3. **Write in the page's language.** A Thai page gets Thai metadata and a Thai llms.txt.
4. **Never change a URL, never add a tracking script.**
5. **You never sign in for the owner and never ask for a password.** Verification happens in their browser. You only ever receive the meta tag they copy out.
6. **Pages that hold customer or personal data are hidden, not promoted.** See "Internal tools" below. When in doubt, ask.
7. **Verify after every phase** by fetching the real URL. Do not report a phase done because the code looks right.

## Phase 0. Look before you touch (2 min)

Find out, by reading the project, not by asking:
- the framework and how routes are served (this skill is written for static HTML, including static HTML served by Hono on SV Cloud; for Next.js prefer metadata exports and next-sitemap, for anything else adapt the same artifacts)
- every public page, and any route that shows private data (`/app`, `/admin`, `/dashboard`, `/api`)
- what already exists: title, description, canonical, Open Graph tags, JSON-LD, robots.txt, sitemap.xml, llms.txt

Then ask the owner exactly two things, in one message:
1. "What is the public address of your site?" It must be the real https address that loads in a browser. If it does not load, stop: deploy first, this skill needs a live site.
2. "Is there anything true about your business that is not on the page yet and that you want machines to know? Address, opening hours, phone, LINE, price range, the area you serve. Say none if not."

## Phase 1. Make the site machine readable (15 min)

Build all of this in one pass, then show a short checklist.

1. **Head basics.** `<title>` under 60 characters and `<meta name="description">` under 155, both saying who this is for and what they get. `<link rel="canonical">` to the public address. `lang` on `<html>`. One `<h1>`, headings in order, `alt` on every image.
2. **Social card.** `og:title`, `og:description`, `og:url`, `og:type`, `og:image`, `twitter:card=summary_large_image`. Make a simple 1200x630 image from the brand colors and the headline, save it in the project, reference it by absolute URL.
3. **One JSON-LD block.** The most specific schema.org type that is honest: `LocalBusiness` or a subtype when there is a physical place customers visit, otherwise `Organization`; add `Product` or `Service` for what is sold; `SoftwareApplication` for an app; `FAQPage` only when the page visibly shows questions and answers. Include only properties you have real values for.
4. **`/robots.txt`.** Allow public pages. Disallow `/api` and any private area. Allow these crawlers by name, because some hosts and firewalls block unknown bots by default: `Googlebot`, `Bingbot`, `GPTBot`, `OAI-SearchBot`, `ChatGPT-User`, `ClaudeBot`, `Claude-SearchBot`, `Claude-User`, `PerplexityBot`, `Google-Extended`, `Applebot`. End with `Sitemap: <address>/sitemap.xml`. Content type `text/plain`.
5. **`/sitemap.xml`.** Every public page, absolute URLs, today's date as `lastmod`. Content type `application/xml`. Private routes never appear here.
6. **`/llms.txt`.** 200 to 400 words of plain facts: who this is, what is offered, who it is for, where, how to get in touch, and links to the key pages. No marketing adjectives. Content type `text/plain`.
7. **A marked empty slot in `<head>`:** `<!-- search console verification tags go here -->`.

Verify: run locally, fetch `/`, `/robots.txt`, `/sitemap.xml`, `/llms.txt`, confirm 200 and the right content type for each. Deploy. Fetch the same four on the public address. Only then continue.

Tell the owner in one line what each of the three files is for, then move on.

## Phase 2. Google Search Console (8 min, the owner clicks, you guide)

Give these one at a time and wait for "done" or a question after each. If they get lost, point them to the drawn screens at https://sv-academy.org/seoaeo.

1. "Open https://search.google.com/search-console/welcome and sign in with your Google account."
2. "You see two boxes. Use the right one, **URL prefix**. Paste `<address>` and press Continue." Why not the left one: the Domain box needs DNS access, and a site on a shared domain (like `*.apps.sv-academy.org`) does not have it.
3. "A list of verification methods opens. Open **HTML tag**, press **Copy**, paste the tag here. Keep that Google tab open."
4. When they paste it: check it is a `<meta name="google-site-verification" ...>` tag, put it in the marked slot on the home page, deploy, fetch the public home page and confirm the tag is in the HTML. Then say: "Go back to the Google tab and press **Verify**."
5. If Verify fails: confirm the tag is in the served HTML of the exact address they entered (https, with or without www, no redirect in between), wait one minute, try again. Never suggest another verification method before this one has been checked properly.

## Phase 3. Sitemap and indexing (4 min)

1. "Left menu, **Sitemaps**. Type `sitemap.xml`, press **Submit**." If it shows "Couldn't fetch" in the first minutes, that is normal for a new property; it is a real problem only if it still says so tomorrow.
2. "Click the search bar at the very top, paste your home address, press Enter. When it says the URL is not on Google, press **Request indexing** and wait about a minute for the confirmation."

## Phase 4. Bing Webmaster Tools (5 min)

Say why first, in one sentence: ChatGPT search and Microsoft Copilot lean on Bing's index, so this is the step that gets the site into AI answers, and almost nobody does it.

1. "Open https://www.bing.com/webmasters/, press Sign in, choose Google, use the same account."
2. "Choose **Import your sites from GSC**, press Import, allow access, tick your site, press Import." Verification and the sitemap come across, no second tag needed.
3. "Left menu, **URL Submission**, Submit URLs, paste your home address, submit."

Fallback when the import does not list the site: "Add your site manually", method **HTML Meta Tag**, they paste the `<meta name="msvalidate.01" ...>` tag to you, you place it next to the Google one, deploy, confirm it is served, they press Verify, then submit `sitemap.xml` under Sitemaps.

## Phase 5. IndexNow (3 min, optional)

Google does not use IndexNow. Bing and the engines that share it do, and they react in minutes.

1. Generate a 32 character lowercase hex key.
2. Serve `/<key>.txt` returning exactly the key, content type `text/plain`. Deploy. Fetch it on the public address.
3. Give the owner one link to open: `https://api.indexnow.org/indexnow?url=<url-encoded home address>&key=<key>`. A blank page or "OK" (HTTP 200 or 202) means accepted. 403 means the key file is not reachable yet. 422 means the URL does not belong to the host of the key.

Offer once to ping IndexNow again whenever they publish a new page. Do not build automation unless they ask.

## Phase 6. Prove it (5 min)

Run these yourself where you can, and give the owner the links where a browser is needed:
- Rich Results Test: `https://search.google.com/test/rich-results?url=<encoded address>`
- Schema validator: `https://validator.schema.org/#url=<encoded address>`
- Share preview: `https://www.opengraph.xyz/url/<encoded address>`

Fix every error without inventing facts. Warnings about optional properties you have no real value for are correct to leave.

Close with a report of five lines: what was added, what was verified on the live address, what the owner submitted, the "Missing facts" list, and the measure plan below.

## The measure plan (give this to the owner, do not skip it)

- Once a day for a week: search `site:<host>` on Google and on Bing. Write down the day it first appears.
- Ask ChatGPT and Perplexity one question a real customer would ask. Screenshot the answer, mentioned or not.
- After a week, open Search Console, Pages and Performance: indexed or not, any impressions, for which words.

Set the expectation honestly: a new address takes from a few days to a few weeks, and no tool can guarantee indexing. Not being indexed yet is information, not failure.

## Internal tools

A booking board, a stock list, a clinic dashboard, anything with customer names, phones, health notes or orders must never appear in a search result. Under Thailand's PDPA that is a data leak, not an SEO problem. For those routes do the opposite of everything above: `Disallow` them in robots.txt, send `X-Robots-Tag: noindex, nofollow`, add a `noindex` meta tag to each page, and keep them out of sitemap.xml. robots.txt alone is not protection, it is a request; if the data is sensitive, tell the owner the page also needs a login before real data goes in. The landing page that sells the business still gets the full treatment.

## What this skill does not do

It does not buy ads, write blog posts, build backlinks, or promise a ranking. It makes a true, well described site easy for machines to read and tells the two indexes that matter that it exists. Everything after that is earned by the business being worth finding.
