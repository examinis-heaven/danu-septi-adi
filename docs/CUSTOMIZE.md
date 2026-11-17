# 🎨 Customize your portfolio

Everything is in **one file**, `index.html`. This guide walks through it section by section. For every change it tells you what to search for (**Ctrl + F**) and what to edit.

> **Time needed:** about 15 minutes for the basics (sections 1–3), and an hour or so to rewrite everything in your own words.

**Before you start**

- **Editor:** use [VS Code](https://code.visualstudio.com) (free). Without installing anything, you can open your repo on GitHub and press the **`.`** key to get VS Code in the browser. Don't use Word or Google Docs: they change `'` into `’` and break the code.
- **Huge lines:** a few lines are enormous because the fonts and the photo are stored as text. Don't edit them; use Ctrl + F to move around. **Alt + Z** turns word-wrap on and off.
- **Check as you go:** double-click `index.html` to open it in your browser and refresh after each change. If the page suddenly loses its animations or the project cards disappear, there's a typo. Press **F12 → Console** and the red error shows the line number.
- **Keep a backup** of the original file.

## Contents

1. [Replace my details with yours](#1-replace-my-details-with-yours)
2. [Your photo](#2-your-photo)
3. [Logo, boot screen, neon sign & favicon](#3-logo-boot-screen-neon-sign--favicon)
4. [Page title, SEO & link previews](#4-page-title-seo--link-previews)
5. [Hero](#5-hero)
6. [Tech marquee](#6-tech-marquee)
7. [About](#7-about)
8. [Terminal](#8-terminal)
9. [Services](#9-services)
10. [Marketing & AI](#10-marketing--ai)
11. [Work](#11-work)
12. [Process](#12-process)
13. [Contact](#13-contact)
14. [Footer](#14-footer)
15. [Colors](#15-colors)
16. [Icons](#16-icons)
17. [Fonts & languages](#17-fonts--languages)
18. [Remove what you don't need](#18-remove-what-you-dont-need)
19. [Final checklist](#19-final-checklist)

---

## 1. Replace my details with yours

Press **Ctrl + H** (⌘ + ⌥ + F on a Mac) and turn on **Match Case** (the `Aa` button, or **Alt + C**). Then use **Replace All** for each row, **in this order**:

| # | Find | Replace with | Example |
|:-:|---|---|---|
| 1 | `fb.com/aanNEION` | your second social link | `linkedin.com/in/janedoe` |
| 2 | `aanneion@gmail.com` | your email | `jane@example.com` |
| 3 | `fiverr.com/aanneion` | your Fiverr profile (or any other profile link) | `fiverr.com/janedoe` |
| 4 | `users/aanneion` | the same, for the Fiverr portfolio link | `users/janedoe` |
| 5 | `aanneion` | your GitHub username | `janedoe` |
| 6 | `Abdullah Al Noman Neion` | your full name | `Jane Doe` |
| 7 | `Neion` | your short name | `Jane` |
| 8 | `neion` | your logo word, in lowercase | `jane` |
| 9 | `Asia/Dhaka` | your [time zone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) | `Europe/Berlin` |
| 10 | `Dhaka` | your city | `Berlin` |
| 11 | `GMT+6` | your UTC offset | `GMT+1` |
| 12 | `Bangladesh` | your country | `Germany` |
| 13 | `https://i.ibb.co.com/7xdhfdMD/github-dp.png` | a public link to your photo | `https://janedoe.github.io/photo.jpg` |

Why it has to be this order, with Match Case on:

- The email and the Fiverr links contain the username, and the username contains the logo word. Replacing top to bottom means nothing gets half-replaced.
- Not on Fiverr? Rows 3 and 4 can point to another profile, or skip them; [Marketing & AI](#10-marketing--ai) shows how to rewrite or remove the Fiverr parts.
- Without Match Case, `neion` would also match `Neion` and `NEION`.
- **Names with an apostrophe** (O'Brien, D'Souza): type the curly **’** instead of `'`. Your name also appears inside the script, and a straight `'` there breaks it.
- The credit comment at the top of the file is written in CAPITALS, so it survives these replacements. Please keep it.

After these replacements:

- The **email** is used everywhere, including the contact form (`const EMAIL` in the script), the copy button and the terminal.
- If your second link **isn't Facebook**, also change its label and icon. See [Contact](#13-contact).
- Also replace the 🇧🇩 flag in the terminal (search `🇧🇩`) and the country code `"addressCountry": "BD"` (see [SEO](#4-page-title-seo--link-previews)).
- Step 12 also changes some demo project texts. That's fine, because you'll replace the demo projects anyway.

---

## 2. Your photo

Use a **square** photo (about 800 × 800 px) with your face in the center. It's shown as a circle and cropped to fill.

**Option A: a separate file (easiest)**

1. Put your photo next to `index.html`, for example as `photo.jpg`, and upload it to the same place.
2. Search for `--dp:url(`. It's the last `<style>` line, near the very end of the file.
3. Triple-click that line to select all of it, and paste:

```html
<style>:root{--dp:url(photo.jpg)}</style>
```

**Option B: keep it a single file**

1. Make the photo small: resize it to about 760 × 760 and export it as WebP or JPEG at roughly 60–100 KB. [Squoosh](https://squoosh.app) does both.
2. Convert it with any "image to Base64" tool. You get text that starts with `data:image/webp;base64,…`.
3. Replace everything between `--dp:url(` and the closing `)` with that text.

**Link previews.** When someone shares your link, apps show the image from `og:image`. That has to be a full public URL, such as your hosted `photo.jpg`. Step 13 of the table above takes care of it.

---

## 3. Logo, boot screen, neon sign & favicon

**Navbar logo.** Search for `class="logo"`. The demo logo is written like this:

```html
<a href="#home" class="logo" aria-label="Jane — back to top">ne<span class="ld">ı</span><span class="fo">o</span>n</a>
```

Replace what's between `>` and `</a>` with your own word. Two optional effects:

| Markup | Effect |
|---|---|
| `<span class="fo">x</span>` | that letter flickers now and then, like a faulty neon tube |
| `<span class="ld">ı</span>` | a dotless **ı** with a glowing pink dot; only use it in place of an "i" |

For example, `ja<span class="fo">n</span>e`. All letters A–Z, a–z, 0–9 and accented Latin letters are available in the neon font.

**Boot screen.** Step 1 already renamed the big neon word. To change the fake terminal lines, search for `fastboot flash portfolio`. The KB number in `Sending 'portfolio' (… KB)` is plain text, so update it if you like.

**Footer neon sign.** Step 1 renamed the word. The line under it is covered in [Footer](#14-footer).

**Favicon (the browser-tab icon).** Search for `rel="icon"` and replace that whole `<link …>` line with the one below. Change the **`J`** to your initial, and the colors if you want:

```html
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 64 64'%3E%3Crect width='64' height='64' rx='14' fill='%2305070a'/%3E%3Ctext x='32' y='45' font-family='Arial,sans-serif' font-size='38' font-weight='700' text-anchor='middle' fill='%237dffb5'%3EJ%3C/text%3E%3Ccircle cx='49' cy='15' r='5' fill='%23ff6ac1'/%3E%3C/svg%3E">
```

(In this kind of link, `%23` stands for `#`. So `%237dffb5` means the color `#7dffb5`.)

---

## 4. Page title, SEO & link previews

Search for `<title>`. The lines just below it control what Google and social apps show:

| Tag | What it is |
|---|---|
| `<title>` | browser tab and search-result title |
| `name="description"` | the search-result snippet (about 150 characters) |
| `name="author"` | your name |
| `og:site_name`, `og:title`, `og:description` | the title and text of link previews |
| `og:image`, `og:image:alt` | the link-preview image (a full public URL) and its description |

**Structured data.** Search for `"@type": "Person"`. That line describes you to search engines. Edit the values inside the quotes: `jobTitle`, `"addressCountry": "BD"` (your two-letter country code), `sameAs` (your profile links) and `knowsAbout`. Keep the quotes, commas and brackets exactly as they are.

---

## 5. Hero

| What | Search for | Notes |
|---|---|---|
| Availability pill | `Available for new projects` | |
| Greeting | `class="hello"` | your name was set in step 1 |
| Headline | `class="hero-title"` | three lines: two fixed lines, then the typing line |
| Typing words | `const words = [` | in the script, e.g. `['websites.', 'online shops.', 'mobile apps.']`; long words shrink to fit the line automatically |
| Intro paragraph | `class="hero-sub"` | |
| Facts row | `class="hero-facts"` | location, Fiverr, languages |
| Floating chips | `class="float f1"` | four chips, `f1`–`f4`; `f2` and `f3` are hidden on phones |
| Build card | `./gradlew assembleRelease` | e.g. `npm run build` / `✓ built in 1.4s` |

- **Headline:** if you change the words, also update the `aria-label` on the `<h1>`. That's the full sentence screen readers read out.
- **Chips:** each one looks like `<svg class="si" style="color:#a78bfa"><use href="#si-kotlin"/></svg>Kotlin`. Change the text, the color and the icon id. The icons you can use are listed in [Icons](#16-icons).

---

## 6. Tech marquee

There are two rows. The first (`<div class="mq-track">`) has **19 items, followed by the same 19 again**. The second (`<div class="mq-track rev">`, which scrolls the other way) has **12 items, then the same 12 again**. Each second copy has `aria-hidden="true"` and makes the loop seamless, so **keep both copies of a row identical**. Search for `class="mq-item"`; each item looks like this:

```html
<span class="mq-item" style="--c:#a78bfa"><svg class="si" aria-hidden="true"><use href="#si-kotlin"/></svg>Kotlin</span>
```

`--c` is the icon's color. Need a logo that isn't in the file yet? See [Icons](#16-icons). Want only one row? Delete the whole `<div class="mq-track rev">…</div>` line.

---

## 7. About

| What | Search for | Notes |
|---|---|---|
| Label, heading, story | `01 — About me` | the four paragraphs follow the heading |
| Quick facts | `class="facts"` | four small cards: based in, speaks, works, focus |
| Stats | `class="stats"` | four animated numbers; the row is designed for exactly four (2 × 2 on phones) |

**How the stats work:**

- `data-count="10"` is the number it counts up to. The visible `10` next to it is what shows when animations are off, so keep both the same.
- `<span class="u">+</span>` is the unit after the number.
- `data-from="99"` makes a stat count **down** instead (the "0 trackers" stat).

---

## 8. Terminal

The terminal's answers are in the `<script>`. Search for `whoami: () =>`. Each command is a small function that returns a list of lines:

| Command | Search for |
|---|---|
| `whoami` | `whoami: () =>` |
| `about` | `about: () => [` |
| `skills` | `skills: () => [` |
| `services` | `services: () => [` |
| `marketing` | `marketing: () => [` |
| `contact` | `contact: () => [` |
| `fiverr` | `fiverr: () =>` |
| `neofetch` | `neofetch: () =>` |
| `cat skills.json` | `'skills.json'` |
| `cat secret.txt` | `'secret.txt'` |
| welcome banner | `interactive portfolio shell` |
| `projects` / `open` | see [Add a project, step 4](ADD-A-PROJECT.md#step-4-optional-add-it-to-the-terminal) |

**Writing terminal lines:**

- Each line is text inside `'…'`. Write `\'` for an apostrophe, `&amp;` for `&` and `&lt;` for `<`.
- To color part of a line, wrap it in a span: `<span class="tg">green</span>`. The classes are `tg` green, `tc` cyan, `tk` pink, `ty` yellow, `tb` indigo, `tw` white and `tm` muted grey.

**Your own neofetch ASCII art.** Search for `id="ascii-art"`; it's in the HTML, inside the terminal block. Generate your name at [patorjk.com/software/taag](https://patorjk.com/software/taag/) (the "Standard" font matches). Paste it between `<script type="text/plain" id="ascii-art">` and `</script>`, replacing the old drawing. Start it on a new line and don't indent it. No escaping is needed. The rows shown next to the art (`name`, `role`, `location`…) are in the script: search `neofetch: () =>`.

---

## 9. Services

Search for `02 — Services`. Each service is one `<article class="card svc"…>` block containing:

- an icon (`<use href="#i-smartphone"/>`; see [Icons](#16-icons)) and a number
- a title, a sentence, four ✓ points and three tags
- a **Get a quote** link with `data-quote="Android app"`. This pre-selects that option in the contact form, so the value must match one of the form options' `value` exactly (see [Contact](#13-contact)).

The 4th card ("Bangla-first Products") is specific to me. Rewrite it or delete the whole `<article>…</article>` block. With an odd number of cards, the last one automatically stretches across the full width.

---

## 10. Marketing & AI

This section shows a **second skill** next to the development work. In the demo it's influencer marketing, virtual assistance and AI, with real Fiverr reviews. Rewrite it for your own second skill (design, writing, video, tutoring…) or remove it.

| What | Search for | Notes |
|---|---|---|
| The whole section | `<!-- ============ marketing & ai` | it ends just before `<!-- ============ work` |
| Heading and intro | `I also grow brands` | the intro paragraph follows |
| Numbers row | `class="mk-kpis"` | four animated numbers; `data-count` works like the [About](#7-about) stats |
| Sample sheet | `id="sheet"` | decorative; see below |
| AI typing bar | `const AI = [` | in the script: icon, name and text for each line |
| Floating badges | `class="mk-badge` | two short claims on the sheet |
| Three skill cards | `class="card svc mk-card"` | same layout as Services; `--ac` is each card's accent color |
| Reviews | `class="card review"` | three quotes, then the name and country |
| Buttons | `Hire me on Fiverr` | the second button opens the contact form |

**The sample sheet** is an illustration labelled "Sample", with made-up, masked handles such as `@jes•••fit`. The rows written in the HTML are what visitors see when animations are off. With animations on, the script fills the rows from `const SETS = [` (two lists of five rows, each with a file name), so edit both places. The status pills (`Vetted`, `Contacted`, `Confirmed`) are set by the script too.

**Reviews:** only use real reviews, word for word, and say where they're from. Keep the `Read all 87 reviews` link and the numbers row in line with your profile.

**Remove the section:** delete from `<!-- ============ marketing & ai` down to the line before `<!-- ============ work`. Then delete the three links to `href="#marketing"` (in `id="nav-links"`, `id="mobile-menu"` and `class="foot-links"`) and renumber the `04 —`, `05 —` and `06 —` labels and the mobile-menu numbers. The script skips the missing parts on its own.

**Not on Fiverr at all?** Search for `fiverr` with Match Case **off**. Apart from the icon in the sprite (`si-fiverr`, which is harmless), the hits are: the hero fact, the Fiverr button in Contact, the footer link, the marketing projects and the tile in [Work](#11-work), the second marquee row, the JSON-LD `sameAs` list and the terminal (`fiverr: () =>`, the `contact` command and a `neofetch` row). Delete them or point them to another profile. The two marketing options of the contact form are covered in [Contact](#13-contact).

---

## 11. Work

| What | Search for |
|---|---|
| Label, heading, intro | `04 — Selected work` |
| Project cards and popups | `const PROJECTS = [`, see **[ADD-A-PROJECT.md](ADD-A-PROJECT.md)** |
| Filter buttons | `data-filter="all"`, see ADD-A-PROJECT.md step 3 |
| Fiverr tile after the cards | `id="proj-more"`: a `<template>`; delete it to remove the tile |
| Big featured card | `class="card featured"` |
| "More on GitHub" button | `More on GitHub` (its link was set in step 1) |

**The featured card** is written by hand in HTML:

- **Text:** a kicker, title, description, four ✓ points, three stats and the buttons with their links.
- **Phone mockup:** decorative. Change its texts (`feather://home`, `Feather`, the `128` counter, `lofi beats to code to`), or swap the logo `<svg viewBox="16 14 76 84"><use href="#feather-logo"/></svg>` for your own SVG, an emoji or text.
- **Its popup** comes from the `PROJECTS` entry with `featured: true` (id `feather`). If you change that id, also change `data-open="feather"` and `data-case="feather"` on the card.
- **Its filter category** is `data-cat="android"` on `<div class="feat-item"`.

---

## 12. Process

Search for `05 — Process`. There are four `<div class="step"…>` blocks. Each has an icon, a `STEP 01` label, a title and a sentence. Add or delete whole blocks; the columns and the line that lights up as you scroll adapt on their own.

---

## 13. Contact

| What | Search for | Notes |
|---|---|---|
| Label, heading, intro | `06 — Contact` | |
| Email card | `class="mail-card"` | done in step 1; the copy button copies `EMAIL` |
| Social buttons | `class="socials"` | GitHub, Fiverr and your second link |
| Local-time line | `id="local-time"` | the time zone is the one from step 1 |
| Status and language lines | `accepting new projects` | the next line is the languages |
| Form options | `name="project"` | six options, described below |
| Success message | `success-text` | plus `'Thanks, '` in the script, the personalized version |
| Email subject line | `_subject:` | the subject of the emails you receive |

**Changing the second link (e.g. Facebook → LinkedIn).** Each social button looks like this:

```html
<a class="social" href="https://fb.com/aanNEION" target="_blank" rel="noopener"><svg class="si" style="color:#1877f2"><use href="#si-facebook"/></svg>Facebook</a>
```

Change the `href`, the label and the icon id (to add a logo, see [Icons](#16-icons)). Also update the same link in four other places:

- the footer links: `class="foot-links"`
- the terminal: search `facebook: () =>` and the `contact` command
- the JSON-LD `sameAs` list (see [SEO](#4-page-title-seo--link-previews))

**Form options.** In each `<label><input type="radio" name="project" value="Website">…Website</label>`, the `value` is what appears in your email and the text at the end is what visitors see. If you rename a value, update the matching `data-quote` on the service cards and the Marketing & AI cards. Delete the `Influencer marketing` and `VA / AI support` options if they don't fit you.

**Where messages go.** Messages are sent to `const EMAIL` at the top of the script. On the live site, send one test message, then click **Activate Form** in the email FormSubmit sends you. After that, every message lands in your inbox. It doesn't work from a file opened on your computer; instead, visitors get a pre-filled email draft.

---

## 14. Footer

| What | Search for |
|---|---|
| Line under the neon sign | `class="sign-sub"` (on phones, the part inside `class="ss-loc"` moves to its own line) |
| Copyright line | `Hand-crafted in a single HTML file` (the year updates itself) |
| Links | `class="foot-links"` |

---

## 15. Colors

Search for `:root{` at the top of the styles:

| Variable | Used for |
|---|---|
| `--grad` | the main gradient on buttons, the headline, stats and highlights |
| `--green`, `--cyan`, `--indigo`, `--pink`, `--yellow` | accent colors (terminal, ticks, dots) |
| `--bg`, `--panel`, `--text`, `--muted` | background and text |

**Changing the neon green completely** takes three Replace Alls:

1. `61,220,132` → your color as R,G,B, e.g. `249,115,22`. This is the green written as RGB, used in all the glows.
2. `#3ddc84` → your hex color, e.g. `#f97316`.
3. Optionally, `#dbffea` and `#dcffea` (the pale glowing text of the logo and sign) → a very light version of your color.

Each project's own colors are its `c1` and `c2` values (see ADD-A-PROJECT.md).

---

## 16. Icons

All icons are stored once, in an SVG sprite at the very top of `<body>`, and reused with `<use href="#id"/>`.

**Already in the file:**

- **Outline icons ([Lucide](https://lucide.dev)), used with `<svg class="i"><use href="#i-…"/></svg>`:** `i-arrow-right` `i-arrow-up` `i-arrow-up-right` `i-badge-check` `i-briefcase` `i-check` `i-clock` `i-code-xml` `i-copy` `i-download` `i-external-link` `i-globe` `i-headset` `i-languages` `i-lock` `i-mail` `i-map-pin` `i-megaphone` `i-message-circle` `i-monitor-smartphone` `i-pen-tool` `i-play` `i-puzzle` `i-quote` `i-rocket` `i-search` `i-send` `i-shield-check` `i-smartphone` `i-sparkles` `i-star` `i-wand-sparkles` `i-x` `i-zap`
- **Brand logos ([Simple Icons](https://simpleicons.org)), used with `<svg class="si"><use href="#si-…"/></svg>`:** `si-android` `si-cloudflare` `si-css` `si-facebook` `si-fiverr` `si-git` `si-github` `si-githubactions` `si-gnubash` `si-googlegemini` `si-googlesheets` `si-gradle` `si-html5` `si-instagram` `si-javascript` `si-jetpackcompose` `si-kotlin` `si-linux` `si-materialdesign` `si-microsoftexcel` `si-netlify` `si-openai` `si-pinterest` `si-react` `si-snapchat` `si-sqlite` `si-tailwindcss` `si-tiktok` `si-typescript` `si-vite` `si-x` `si-youtube`

**Adding an icon.** Search for `style="position:absolute;width:0;height:0;overflow:hidden">`. That's the end of the sprite's opening tag. Paste your new `<symbol>` right after it:

- **An outline icon:** on lucide.dev, open the icon, click **Copy SVG**, and keep only the tags inside `<svg>…</svg>`:

  ```html
  <symbol id="i-heart" viewBox="0 0 24 24"><path d="M2 9.5a5.5 5.5 0 0 1 9.591-3.676.56.56 0 0 0 .818 0A5.49 5.49 0 0 1 22 9.5c0 2.29-1.5 4-3 5.5l-5.492 5.313a2 2 0 0 1-3 .019L5 15c-1.5-1.5-3-3.2-3-5.5"/></symbol>
  ```

- **A brand logo:** on simpleicons.org, download the SVG and copy its `d="…"` path:

  ```html
  <symbol id="si-python" viewBox="0 0 24 24"><path d="…the path from the downloaded file…"/></symbol>
  ```

Then use it anywhere, e.g. `<svg class="si"><use href="#si-python"/></svg>`.

---

## 17. Fonts & languages

- **What's covered:** the embedded fonts (Inter, Space Grotesk, JetBrains Mono, and Tilt Neon for the logo) contain English and Western-European characters, including accents like é, ü, ñ and ø.
- **Other alphabets** (Cyrillic, Greek, Arabic, Devanagari…) still display correctly using the visitor's built-in fonts.
- **Bangla:** the demo uses a tiny Bangla font with only the few letters it needs. If you don't write in Bangla, delete the `<span lang="bn">…</span>` bits; search `lang="bn"`. If you do, new Bangla letters will use the visitor's built-in Bangla font.
- **Using different fonts:** the simplest way is to add a Google Fonts `<link>` in the `<head>`, then change `--font` (text), `--display` (headings), `--mono` (code) and `--neon` (logo) in `:root{`. This adds an external request, so the page is no longer fully self-contained.
- **Page language:** the first line is `<html lang="en">`. Change `en` if your site is in another language.

---

## 18. Remove what you don't need

Everything below can be deleted safely; the script skips anything that's missing.

> **Tip:** in VS Code, click the small arrow to the left of a block's first line to fold it. Then you can select the folded line and delete the whole block in one go.

| To remove | Delete | Also |
|---|---|---|
| Boot screen | from `<!-- ============ boot screen` down to the line before `<!-- ============ navigation` | nothing |
| Terminal | the whole `<div class="term-col"…>…</div>` block | nothing; the About text becomes one column automatically |
| Tech marquee | from `<!-- ============ tech marquee` to the line before `<!-- ============ about` | nothing |
| Second marquee row only | the `<div class="mq-track rev">…</div>` line | nothing |
| Marketing & AI section | from `<!-- ============ marketing & ai` to the line before `<!-- ============ work` | remove its three `href="#marketing"` links and renumber the labels (see [Marketing & AI](#10-marketing--ai)) |
| Fiverr tile in the project grid | the `<template id="proj-more">…</template>` block | nothing |
| Stats | the `<div class="stats"…>…</div>` block | nothing |
| A whole section (e.g. Process) | its `<section …>…</section>` block | remove its links in `id="nav-links"`, `id="mobile-menu"` and `class="foot-links"`, and renumber the `01 —`, `02 —`… labels |
| Konami easter egg | search `overdrive` | optional; it's harmless |

---

## 19. Final checklist

- [ ] Opened `index.html` locally: no red errors in **F12 → Console**.
- [ ] Checked on a phone, or in DevTools' device mode (**Ctrl + Shift + M**).
- [ ] Every link works: email, GitHub, socials, project buttons.
- [ ] `og:image` is a full public URL, so link previews show your photo.
- [ ] After deploying, sent a test message and clicked **Activate Form** in FormSubmit's email.
- [ ] Optional: ran Lighthouse (DevTools → Lighthouse) for a quick health check.

Happy shipping! ✨
