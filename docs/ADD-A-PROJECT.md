# ➕ How to add a new project to your portfolio

Projects live inside `index.html`. You don't need build tools or installs, only a text editor. Plan on about 10 minutes per project.

> New here? Do the basics in **[CUSTOMIZE.md](CUSTOMIZE.md)** first (your name, email, photo), then come back to add your work.

## The short version

| # | What you do | Where to paste it (Ctrl+F and search for…) | Needed? |
|---|---|---|---|
| 1 | Paste a **project block** | `id: 'liar'` | ✅ yes |
| 2 | Paste an **animated icon** | `const FEATHER_SVG` | ⭐ recommended |
| 3 | Raise the **filter numbers** | `data-filter="all"` | ✅ yes |
| 4 | Add it to the **terminal** | `const OPEN` | optional |
| 5 | Update the **"10+" stat** | `data-count="10"` | optional |
| 6 | **Test** on your PC, then **upload** | — | ✅ yes |

Once the block is in, the new card gets all of the site's motion automatically. You don't have to write any animation code for these:

- the scroll-in reveal, staggered with the cards around it
- a 3-D tilt and a cursor spotlight in **your** colours (on desktop)
- the icon zooming and tilting on hover
- the animated shuffle when someone clicks a filter
- a full case-study popup in your colours, with keyboard support and Esc to close

The only piece of art you add yourself is the small animated icon on the card (step 2). There are ready-made templates for it.

> 💡 **Quickest way:** paste the blocks exactly as they are, using the placeholder name `myapp`. Then run one **Replace All** from `myapp` to your project's id, for example `weatherly`. That renames the project, its icon and the terminal entry in one go. (The template link URLs contain `myapp` too, so check them afterwards.)

---

## Before you start: pick an editor

- **Best option:** [VS Code](https://code.visualstudio.com) (free) on your PC.
- **Without installing anything:** open your repository on GitHub and press the **`.`** key. A full VS Code (github.dev) opens in the browser. Edit the file, then commit from the Source Control tab on the left.
- **Don't use** Word, WordPad or Google Docs. They replace `'` with `’` and break the code.

A few lines in the file are **enormous**, because your photo and the fonts are stored inside it as text. Don't edit them; use Ctrl+F to move around. In VS Code, **Alt+Z** turns word-wrap on and off if those lines get in the way.

Keep a copy of the working `index.html` before you start editing.

---

## Step 1: paste the project block

1. Press Ctrl+F and search for `id: 'liar'`.
2. The line directly **above** it contains only `  {`. Put the cursor at the start of that `{` line and paste the block below. The block ends with `},`, so nothing else needs to change.
3. Fill in your own text.

Your project will show up **first** in the Work grid, which is a good place for your newest work. To put it somewhere else, paste it above the `{` of the project it should come before. The grid shows projects in the same order as this list.

> Already deleted the demo projects? Paste your block right after the featured project's block (the one with `featured: true`), after its closing `},`.

<!-- snippet:project -->
```js
  {
    id: 'myapp',                          // unique · lowercase letters/numbers only
    title: 'My New App',
    kicker: 'Productivity · Android app', // the small coloured line above the title
    cat: 'android',                       // 'android', 'web', 'tools' or 'marketing' — or several: 'web tools'
    c1: '#4ade80', c2: '#0ea5e9',         // your accent colours (glow, gradients, popup theme)
    icon: 'myapp',                        // which illustration to show — see step 2
    short: 'One or two sentences for the card: what it is and why it is cool.',
    tags: ['Kotlin', 'Jetpack Compose', 'Room'],
    tagline: 'A punchy one-liner shown under the title in the popup.',
    overview: 'A short paragraph for the popup: the problem, who it is for and what you built.',
    highlights: [
      'A key feature or result.',
      'Another key feature or result.',
      'One more (3–6 bullets works best).'
    ],
    stack: ['Kotlin', 'Jetpack Compose', 'Material 3', 'Room'],
    links: [
      { label: 'Download APK', short: 'Download', href: 'https://github.com/your-username/myapp/releases/latest', icon: 'i-download' },
      { label: 'Source code', short: 'Code', href: 'https://github.com/your-username/myapp', icon: 'si-github' }
    ]
  },
```

### What each field does

| Field | Where it shows | Notes |
|---|---|---|
| `id` | nowhere; it's the project's internal name | Must be unique. Use only `a–z` and `0–9`, e.g. `weatherly` or `shop2`. |
| `title` | card and popup | |
| `kicker` | small line above the title | Shown in capitals automatically. Separate words with ` · ` like the other projects. |
| `cat` | filter buttons | `android`, `web`, `tools` or `marketing`, or a category you add yourself (step 3). For more than one, separate with spaces: `'web tools'`. |
| `c1`, `c2` | card glow, cover gradient, popup colours, tick marks | Any hex colours. `c1` is the main one. |
| `icon` | card cover and popup | The name of an icon in `ICONS` (see step 2). |
| `short` | card text | 1–2 sentences (120–170 characters) keeps the cards the same height. |
| `tags` | small chips on the card | 2 or 3 short words. |
| `tagline` | popup, under the title | One line. |
| `overview` | popup, first paragraph | |
| `highlights` | popup, list with ✓ marks | 3–6 bullets. |
| `stack` | popup, chips under "Built with" | |
| `stackLabel` | popup, the heading above those chips | Optional. Leave it out to keep "Built with"; the marketing projects use `'Tools & deliverables'`. |
| `links` | card and popup | See below. |

**Links:**

- Every link becomes a button in the popup. The first one is the bright, highlighted button.
- A link that also has a `short` name appears on the card too (at most 2 per card).
- For `icon`, use one of `i-download`, `i-play`, `i-external-link`, `i-globe`, `si-github` or `si-fiverr`. The full list is in the appendix.

### Three text rules (this is where JavaScript breaks)

1. **Apostrophes inside `'…'` text** need a backslash: `'It\'s fast'`. You can also use the curly apostrophe: `'It’s fast'`.
2. **Commas:** list items are separated by commas, and every project block ends with `},`.
3. **Only straight quotes around text:** `'…'`, never `‘…’` or `“…”`.

You can type Bangla directly, e.g. `short: 'বাংলায় লেখা যাবে'`. It will display correctly, but new Bangla letters use the visitor's built-in Bangla font. The embedded Hind Siliguri font only contains the few letters the site uses today.

---

## Step 2: add an animated icon

Each card cover shows a small 84 × 84 SVG with its animation built in. The animation uses SVG tags such as `<animate>` (this is called SMIL). The icons are stored in a list called `ICONS`. You have three options:

### Option A: reuse an existing icon (10 seconds)

Set `icon:` to `'liar'`, `'2fa'`, `'doico'`, `'bau'`, `'bangla'` or `'roms'`. Don't use `'feather'`; it only works for the big featured card.

### Option B: start from a template (5 minutes) ⭐

Two animated templates in the site's style are included:

| Template | Best for | What moves |
|---|---|---|
| **App tile** ([`icon-templates/app-tile.svg`](icon-templates/app-tile.svg)) | Android apps | tile floats, ripple, orbiting dot, shine sweep |
| **Browser window** ([`icon-templates/browser-window.svg`](icon-templates/browser-window.svg)) | websites & web apps | window floats, loading bar, text lines fade in, cursor click |

To watch one play, open the `.svg` file in your browser (double-click it, or drag it into a Chrome tab).

To use one:

1. Press Ctrl+F and search for `const FEATHER_SVG`. Add an empty line **above** it.
2. Paste the matching block from below onto that empty line.
3. Rename `myapp` (or `mysite`) to your project id. The Replace All from the tip at the top does this, and it also renames the internal ids such as `myapp-grad`.
4. Change the two `stop-color` values to your `c1` and `c2`. In the app tile, the orbiting dot uses colour 1 as well.
5. Swap in your own glyph. On [lucide.dev](https://lucide.dev/icons), pick any icon and click **Copy SVG**. Paste only the tags inside it (`<path …/>`, `<rect …/>`, `<circle …/>`) where the example glyph is, at the comment marked **YOUR GLYPH**.

**App tile**

<!-- snippet:icon-app -->
```js
ICONS.myapp = `
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 84 84" aria-hidden="true">
  <!-- Starter icon: "App tile" (great for Android apps).
       Find & Replace  myapp  with your project id, then change the two colours. -->
  <defs>
    <linearGradient id="myapp-grad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0" stop-color="#4ade80"/>   <!-- colour 1 (use the same as c1) -->
      <stop offset="1" stop-color="#0ea5e9"/>   <!-- colour 2 (use the same as c2) -->
    </linearGradient>
    <linearGradient id="myapp-shine" x1="0" y1="0" x2="1" y2="0">
      <stop offset="0" stop-color="#fff" stop-opacity="0"/>
      <stop offset=".5" stop-color="#fff" stop-opacity=".5"/>
      <stop offset="1" stop-color="#fff" stop-opacity="0"/>
    </linearGradient>
    <clipPath id="myapp-clip"><rect x="17" y="17" width="50" height="50" rx="14"/></clipPath>
  </defs>

  <!-- A. ripple that pulses out from behind the tile -->
  <circle cx="42" cy="42" r="31" fill="none" stroke="url(#myapp-grad)" stroke-width="1.6">
    <animate attributeName="r" values="31;40" dur="2.8s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values=".9;0" dur="2.8s" repeatCount="indefinite"/>
  </circle>

  <!-- B. faint orbit + a dot travelling around it -->
  <circle cx="42" cy="42" r="37" fill="none" stroke="#fff" stroke-opacity=".14" stroke-dasharray="1.5 4.5"/>
  <g>
    <animateTransform attributeName="transform" type="rotate" from="0 42 42" to="360 42 42" dur="9s" repeatCount="indefinite"/>
    <circle cx="42" cy="5" r="2.6" fill="#4ade80"/>
  </g>

  <!-- C. the app tile, gently floating -->
  <g>
    <animateTransform attributeName="transform" type="translate" values="0 0;0 -3;0 0" dur="4s" repeatCount="indefinite"/>
    <rect x="17" y="17" width="50" height="50" rx="14" fill="url(#myapp-grad)"/>
    <rect x="17.5" y="17.5" width="49" height="49" rx="13.5" fill="none" stroke="#fff" stroke-opacity=".25"/>

    <!-- D. a light shine that sweeps across the tile every few seconds -->
    <g clip-path="url(#myapp-clip)">
      <rect x="-20" y="8" width="18" height="70" fill="url(#myapp-shine)" transform="skewX(-18)">
        <animate attributeName="x" values="-20;-20;120" keyTimes="0;.55;1" dur="4.5s" repeatCount="indefinite"/>
      </rect>
    </g>

    <!-- E. YOUR GLYPH: paste the inside of any 24x24 icon from lucide.dev here
         (this one is Lucide "smartphone") -->
    <g transform="translate(28 28) scale(1.1667)" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
      <rect width="14" height="20" x="5" y="2" rx="2"/>
      <path d="M12 18h.01"/>
    </g>
  </g>
</svg>`;
```

**Browser window**

<!-- snippet:icon-web -->
```js
ICONS.mysite = `
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 84 84" aria-hidden="true">
  <!-- Starter icon: "Browser window" (great for websites & web apps).
       Find & Replace  mysite  with your project id, then change the two colours. -->
  <defs>
    <linearGradient id="mysite-grad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0" stop-color="#fb7185"/>   <!-- colour 1 (use the same as c1) -->
      <stop offset="1" stop-color="#f59e0b"/>   <!-- colour 2 (use the same as c2) -->
    </linearGradient>
  </defs>

  <!-- A. the window, gently floating -->
  <g>
    <animateTransform attributeName="transform" type="translate" values="0 0;0 -2.5;0 0" dur="4.5s" repeatCount="indefinite"/>
    <rect x="9" y="15" width="66" height="52" rx="7" fill="#10151c" stroke="url(#mysite-grad)" stroke-width="2"/>
    <circle cx="17" cy="23" r="2" fill="#ff5f57"/>
    <circle cx="23.5" cy="23" r="2" fill="#febc2e"/>
    <circle cx="30" cy="23" r="2" fill="#28c840"/>
    <rect x="36" y="20" width="31" height="6" rx="3" fill="#fff" fill-opacity=".09"/>

    <!-- B. page-loading bar -->
    <rect x="10" y="30" width="0" height="2" fill="url(#mysite-grad)">
      <animate attributeName="width" values="0;64;64" keyTimes="0;.6;1" dur="3.6s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="1;1;0" keyTimes="0;.75;1" dur="3.6s" repeatCount="indefinite"/>
    </rect>

    <!-- C. page content: a hero block + text lines that fade in one by one -->
    <rect x="16" y="38" width="22" height="22" rx="4" fill="url(#mysite-grad)"/>
    <!-- YOUR GLYPH (optional): a 24x24 Lucide icon, shrunk to fit the block (this one is "globe") -->
    <g transform="translate(19.5 41.5) scale(.625)" fill="none" stroke="#fff" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round">
      <circle cx="12" cy="12" r="10"/>
      <path d="M12 2a14.5 14.5 0 0 0 0 20 14.5 14.5 0 0 0 0-20"/>
      <path d="M2 12h20"/>
    </g>
    <rect x="43" y="39" width="24" height="4" rx="2" fill="#fff" fill-opacity=".6">
      <animate attributeName="opacity" values="0;1;1;0" keyTimes="0;.2;.85;1" dur="3.6s" repeatCount="indefinite"/>
    </rect>
    <rect x="43" y="47" width="19" height="3" rx="1.5" fill="#fff" fill-opacity=".3">
      <animate attributeName="opacity" values="0;0;1;1;0" keyTimes="0;.15;.35;.85;1" dur="3.6s" repeatCount="indefinite"/>
    </rect>
    <rect x="43" y="53" width="22" height="3" rx="1.5" fill="#fff" fill-opacity=".3">
      <animate attributeName="opacity" values="0;0;1;1;0" keyTimes="0;.3;.5;.85;1" dur="3.6s" repeatCount="indefinite"/>
    </rect>
  </g>

  <!-- D. a mouse pointer that moves in and "clicks" -->
  <g>
    <animateTransform attributeName="transform" type="translate" values="10 8;0 0;0 0;10 8" keyTimes="0;.35;.75;1" dur="3.6s" repeatCount="indefinite"/>
    <path d="M58 55 v15 l4 -3.6 l3 6.2 l3 -1.5 l-3 -6 l5.2 -.4 z" fill="#fff" stroke="#0b0f14" stroke-width="1.2" stroke-linejoin="round"/>
  </g>
</svg>`;
```

> The icon is wrapped in **backticks** `` ` `` (the key under Esc), not quotes. That's what lets it run over several lines. Don't forget the `;` at the end.

### Option C: draw your own, or have an AI make one

Any SVG works if it follows these rules:

- Use `viewBox="0 0 84 84"` with no background (the card already has a glow and a grid behind it). Keep everything inside the box.
- Animate only with SVG animation tags (`<animate>`, `<animateTransform>`). Do **not** add `<style>` or `<script>`, because a `<style>` inside one icon affects the whole page.
- Start every `id` with your project id, e.g. `id="myapp-glow"` and `url(#myapp-glow)`. If two icons use the same id, one of them takes the other's colours. The popup copy of the icon handles this on its own.
- Keep it small (under about 5 KB) and keep the motion gentle and looping.

A prompt you can give an AI (fill in the brackets):

```text
Create an animated SVG icon for a portfolio project card.
Project: [name] — [one line about what it does]
Rules: viewBox="0 0 84 84", no width/height, transparent background, it sits on a dark #0a0e14 card.
Colours: [c1] and [c2], plus white.
Style: clean flat illustration, 2–3 px strokes, rounded caps, everything inside the box with ~6 px margin.
Animation: 1–3 subtle, seamless, infinitely looping SMIL animations (<animate>, <animateTransform>).
No <style>, no <script>, no text, no external images or fonts.
Prefix every id with "[id]-". Keep it under 4 KB.
```

Then wrap the result in ``ICONS.yourid = `…`;`` and paste it above `const FEATHER_SVG`, the same way as in option B.

### Animation cheat-sheet

Put each line **inside** the element (or the `<g>` group) you want to animate.

<!-- snippet:cheats -->
```xml
<!-- Float up & down (put it inside a <g> wrapped around the part that should float) -->
<animateTransform attributeName="transform" type="translate" values="0 0;0 -3;0 0" dur="4s" repeatCount="indefinite"/>

<!-- Spin around the centre of the 84×84 box -->
<animateTransform attributeName="transform" type="rotate" from="0 42 42" to="360 42 42" dur="8s" repeatCount="indefinite"/>

<!-- Pulse / breathe (any element) -->
<animate attributeName="opacity" values="1;.35;1" dur="2s" repeatCount="indefinite"/>

<!-- Ripple: inside a <circle>, use both lines together -->
<animate attributeName="r" values="20;38" dur="2.5s" repeatCount="indefinite"/>
<animate attributeName="opacity" values="1;0" dur="2.5s" repeatCount="indefinite"/>

<!-- Colour shift (use attributeName="stroke" for outlines) -->
<animate attributeName="fill" values="#4ade80;#0ea5e9;#4ade80" dur="6s" repeatCount="indefinite"/>

<!-- Blink, like a terminal cursor -->
<animate attributeName="opacity" values="1;0" calcMode="discrete" dur="1s" repeatCount="indefinite"/>

<!-- Scan line: inside a <rect>, moves it down and back up -->
<animate attributeName="y" values="10;70;10" dur="3s" repeatCount="indefinite"/>

<!-- A line that draws itself, pauses, then rewinds. Goes inside a <path> that has pathLength="100" stroke-dasharray="100" -->
<animate attributeName="stroke-dashoffset" values="100;0;0;100" keyTimes="0;.4;.8;1" dur="5s" repeatCount="indefinite"/>

<!-- Eased (smooth) float instead of linear: keyTimes + calcMode + one keySpline per gap -->
<animateTransform attributeName="transform" type="translate" values="0 0;0 -3;0 0" keyTimes="0;.5;1" calcMode="spline" keySplines=".45 0 .55 1;.45 0 .55 1" dur="4s" repeatCount="indefinite"/>
```

Two things to know:

- Each element can run only **one** transform animation. To make something float **and** spin, nest two `<g>` groups and give each one a single animation.
- If an element already has a `transform="…"` attribute, put the animation on a `<g>` around it. Otherwise the animation replaces the existing transform. The glyph in the app-tile template is set up this way.

---

## Step 3: raise the filter numbers

Press Ctrl+F and search for `data-filter="all"`. You'll find five buttons. The number inside `<span class="n">…</span>` is that button's count:

<!-- snippet:filters -->
```html
<button type="button" aria-pressed="true" data-filter="all">All<span class="n">9</span></button>
<button type="button" aria-pressed="false" data-filter="android">Android<span class="n">2</span></button>
<button type="button" aria-pressed="false" data-filter="web">Web<span class="n">5</span></button>
<button type="button" aria-pressed="false" data-filter="tools">Tools<span class="n">3</span></button>
<button type="button" aria-pressed="false" data-filter="marketing">Marketing<span class="n">2</span></button>
```

- **All** counts every project, including the featured one. Add 1 for each new project.
- **Android / Web / Tools / Marketing** count the projects that have that word in `cat`. Add 1 to each word your new project uses.

For example, adding one Android app (`cat: 'android'`) makes All `10` and Android `3`. The others stay the same.

The green Fiverr tile at the end of the grid isn't a project, so it isn't counted. It comes from `<template id="proj-more">` in the HTML and always stays last; delete that template if you don't need the tile.

**To add a new category** such as *Games*:

1. Copy the Tools line and paste the copy right below it.
2. In the copy, change `data-filter="tools"` to `data-filter="games"`, change the label `Tools` to `Games`, and set the number.
3. Add the same word to the project's `cat`, e.g. `cat: 'web games'`.

The filtering and the sliding highlight pick up the new button on their own. On small phones the filter bar can be swiped sideways once it runs out of room.

---

## Step 4 (optional): add it to the terminal

The terminal in the About section keeps its own list. If you skip this step, everything else still works; the project just won't appear when visitors type `projects` or `open`.

There are four small edits (the example id is `myapp`):

**a) The `projects` list.** Search for `projects: () => [` and add this line right below it (or below any other line of that list):

<!-- snippet:term-projects -->
```js
      ['myapp', 'My New App — one-line description'],
```

Keep the first part at 8 characters or fewer so the columns line up.

**b) The `open` command.** Search for `const OPEN = {` and type `myapp: 'myapp', ` right after the `{`:

<!-- snippet:term-open -->
```js
  const OPEN = { myapp: 'myapp', feather: 'feather', featherbrowser: 'feather', …
```

The left side is what visitors type (lowercase letters and numbers only). The right side is your project `id`. You can add nicknames as well, e.g. `weather: 'myapp',`.

**c) Tab-completion.** Search for `pool = prefix === 'open '` and type `'myapp', ` right after the `[`:

<!-- snippet:term-pool -->
```js
      pool = prefix === 'open ' ? ['myapp', 'feather', 'liar', …
```

**d) The help hint.** Search for `&lt;feather | liar` and type `myapp | ` right after `&lt;`.

---

## Step 5 (optional): update the numbers

- **"10+ projects shipped"** in About: search for `data-count="10"` and change both numbers on that line (`data-count="10">10<`).
- **The terminal's neofetch line:** search for `10+ shipped`.

---

## Step 6: test, then upload

**Test on your PC.** Double-click `index.html` and scroll to **Work**. Check that:

- the card shows up
- the icon animates
- the card tilts on hover
- **Details** opens the popup
- the filter numbers are right

The contact form won't send from your PC. That's expected; it only works on the live site.

**If something broke,** you'll see the project cards missing, or the page appearing after a few seconds with no animations at all. That means a typo. Press **F12** and open **Console**: the red error shows the line number. Almost always it's one of these:

- a missing comma between blocks (`}` where there should be `},`)
- an apostrophe without a backslash (`'It's'` should be `'It\'s'`)
- a missing closing backtick or `;` after an icon
- curly quotes `‘ ’ “ ”` around text

**Publish.** If you edited in github.dev, commit from the Source Control tab. If you edited on your PC, open your repository on GitHub, choose **Add file → Upload files**, drop in the new `index.html` (it replaces the old one) and click **Commit changes**. GitHub Pages updates in 1–2 minutes. Press **Ctrl+F5** to skip the browser cache.

---

## Other quick edits

- **Change a project's text:** edit its block.
- **Reorder projects:** move whole blocks, from the `{` line through the `},` line.
- **Remove a project:** delete its block, lower the filter numbers and remove its terminal lines from step 4.
- **Start fresh:** delete the demo projects' blocks (keep one as a pattern until you've added your own), set the filter numbers, and clean up the terminal lists from step 4. The demo icons in `ICONS` can stay; unused icons don't show anywhere.

## About the big "Featured" card

The large featured card with the phone mockup (Feather Browser in the demo) is written in HTML by hand; it isn't generated from the list. Only its popup comes from the entry with `featured: true`. Give `featured: true` to **one** project only, the one shown in the big card; on any other project it would hide that project's card. To change what the featured card says, see [CUSTOMIZE.md → Work](CUSTOMIZE.md#11-work).

---

## Appendix: link icons in the file

The page only includes the icons it actually uses, so choose link icons from this list. If you use a name that isn't here, the button still works but shows no icon.

**General:** `i-download` `i-play` `i-external-link` `i-globe` `i-arrow-right` `i-arrow-up` `i-arrow-up-right` `i-badge-check` `i-briefcase` `i-check` `i-clock` `i-code-xml` `i-copy` `i-headset` `i-languages` `i-lock` `i-mail` `i-map-pin` `i-megaphone` `i-message-circle` `i-monitor-smartphone` `i-pen-tool` `i-puzzle` `i-quote` `i-rocket` `i-search` `i-send` `i-shield-check` `i-smartphone` `i-sparkles` `i-star` `i-wand-sparkles` `i-x` `i-zap`

**Brands:** `si-github` `si-android` `si-facebook` `si-fiverr` `si-kotlin` `si-jetpackcompose` `si-materialdesign` `si-react` `si-typescript` `si-javascript` `si-html5` `si-css` `si-tailwindcss` `si-vite` `si-netlify` `si-cloudflare` `si-git` `si-githubactions` `si-gradle` `si-sqlite` `si-linux` `si-gnubash` `si-openai` `si-googlegemini` `si-instagram` `si-tiktok` `si-youtube` `si-x` `si-pinterest` `si-snapchat` `si-googlesheets` `si-microsoftexcel`
