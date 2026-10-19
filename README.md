<div align="center">

<img src="assets/icon.svg" width="88" height="88" alt="RW ThreadSmith anvil icon">

# RW ThreadSmith

**Sell your ranked-war gear with a forum post that stands out, not another generic list.**
Sync your bazaar, inventory or Item Market, price everything in one vault, and export polished images of your shop ready to drop into a Torn forum post.

[![Version](https://img.shields.io/badge/version-6.2.1-82c91e?style=flat-square&labelColor=222)](https://greasyfork.org/scripts/575393)
[![License](https://img.shields.io/badge/license-GPL--3.0-74c0fc?style=flat-square&labelColor=222)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Torn.com-e0b73e?style=flat-square&labelColor=222)](https://www.torn.com/forums.php)
[![Torn PDA](https://img.shields.io/badge/Torn%20PDA-supported-b197fc?style=flat-square&labelColor=222)](https://github.com/Manuito83/torn-pda)
[![Free](https://img.shields.io/badge/price-FREE-82c91e?style=flat-square&labelColor=222)](#)

[Install](#installation) &nbsp;·&nbsp; [Quickstart](#quickstart) &nbsp;·&nbsp; [Designs](#designs) &nbsp;·&nbsp; [API keys](#api-keys) &nbsp;·&nbsp; [Torn PDA](#torn-pda) &nbsp;·&nbsp; [FAQ](#faq) &nbsp;·&nbsp; [Changelog](#changelog)

</div>

---

> [!NOTE]
> **TL;DR** Install, open any Torn forum page, click **RW ThreadSmith** in your **My Forums** list, paste an API key and press **Sync**. Pick a design, press **Generate images**, save them, and add them to your post in order.

## What it does

RW ThreadSmith lives inside Torn's own forum page. It reads your listings through the Torn API, keeps them in a permanent vault, and renders your shop as high-resolution images in one of 14 designs. Images get around the problems with HTML threads: no fighting the forum editor, no character limits, and no layouts breaking on phones.

- **Built into the forum page.** A row in your **My Forums** list opens the tool right inside the page. It uses Torn's own colours, so it follows dark and light mode automatically.
- **Three sync sources.** Bazaar, inventory or Item Market, each labelled with the API key level it needs.
- **Permanent vault.** Every ranked-war item you sync is kept. Mark items Sold or Hidden instead of losing them when they leave your bazaar.
- **14 designs**, each with curated palettes, colour pickers, corner radius and spacing options.
- **Auto-split.** Long shops are split into numbered images at clean breaks between items, with clear file names.
- **Mug-protection markup.** Pad your listings against buy-muggers and have the padding stripped from the prices in your images. [Details below.](#mug-protection-markup)
- **Two-level sorting and grouping**, set separately for weapons and armor.
- **Works in Torn PDA.** Uses PDA's API key automatically, and saves images through the phone's share sheet.

```mermaid
flowchart LR
    K["API key"] --> S["Sync<br/>bazaar · inventory · item market"]
    S --> V["Vault<br/>prices · status · notes"]
    V --> O["Output<br/>design · palette · sorting"]
    O --> I["PNG images<br/>auto-split, numbered"]
    I --> P["Torn forum post"]
```

---

## Where it lives

The script adds one row to your **My Forums** list, right after **My Company** (or before **Donator Forum** if you have no company). Click it to open the tool inside the page; click again to close it. The row's count shows how many items are currently active in your vault.

<div align="center">
<img src="assets/forum-row.png" alt="The RW ThreadSmith row in the My Forums list, in Torn's dark and light themes" width="820">
<br><sub>The same row in Torn's dark and light mode. Everything is styled from Torn's own theme variables.</sub>
</div>

### The four tabs

<table>
  <tr>
    <td align="center" width="50%" valign="top">
      <img src="assets/panel-load.png" alt="Sync tab" width="380"><br>
      <sub><b>Sync</b>: your API key, the key level the chosen source needs, vault status, backup and restore.</sub>
    </td>
    <td align="center" width="50%" valign="top">
      <img src="assets/panel-items.png" alt="Vault tab" width="380"><br>
      <sub><b>Vault</b>: search, filter, bulk actions, and per-item status, price and notes.</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%" valign="top">
      <img src="assets/panel-gen.png" alt="Output tab" width="380"><br>
      <sub><b>Output</b>: header text, layout and sorting, design, palette, colours and image options.</sub>
    </td>
    <td align="center" width="50%" valign="top">
      <img src="assets/panel-cfg.png" alt="Config tab" width="380"><br>
      <sub><b>Config</b>: sync source, vault card display, mug-protection markup, image options.</sub>
    </td>
  </tr>
</table>

---

## Installation

You need a userscript manager, or the Torn PDA app.

| Where | What to use |
|---|---|
| Chrome, Edge, Brave, Opera | [Tampermonkey](https://www.tampermonkey.net/) |
| Firefox | [Tampermonkey](https://www.tampermonkey.net/) or [Violentmonkey](https://violentmonkey.github.io/) |
| Safari | [Tampermonkey](https://www.tampermonkey.net/) |
| Phone | [Torn PDA](https://github.com/Manuito83/torn-pda) (see [Torn PDA](#torn-pda)) |

1. **[⬇ Install from Greasy Fork](https://greasyfork.org/scripts/575393)** and confirm in your manager.
2. Open any page on `torn.com/forums.php`.
3. Click **RW ThreadSmith** in your **My Forums** list.

> [!IMPORTANT]
> The script only runs on `torn.com/forums.php`. The first time you generate images, Tampermonkey may ask to allow connections to Google Fonts (for the design typefaces) and `www.torn.com` (for item artwork). Allow them once.

---

## Quickstart

### 1. Sync your items

Open the **Sync** tab, paste your API key and press **Sync**. Choose where to sync from in **Config → Sync Source**:

| Source | What it reads | Prices |
|---|---|---|
| **Bazaar** (default) | Your bazaar listings | Your bazaar prices |
| **Inventory** | Primary, Secondary, Melee and Defensive items in your inventory | None, set them in the Vault |
| **Item Market** | Your Item Market listings | Your Item Market prices |

Only **ranked-war items** are kept: yellow, orange or red rarity with at least one bonus. Plain and white items are skipped. Faction-owned armory items are skipped on inventory syncs.

Syncing is paced at about 85 requests per minute to protect your key. Items already in the vault need no extra lookup, so later syncs are fast. You can cancel at any time and keep what was fetched.

### 2. Review the vault

The **Vault** tab lists every synced item with its rarity, stats, bonuses and whether it is currently listed.

- **Status**: `Active` items appear in your images, `Sold` items can show as sold, `Hidden` items are left out.
- **Price**: leave it blank to use the automatic price (your listing price with [mug markup](#mug-protection-markup) removed, shown as `Auto: ...`), or type your own such as `5m`, `1.5b` or `750k`.
- **Note**: turn on the notes field in Config to annotate any item. Notes can also appear in the images.

Bulk actions apply to whatever the current search and filters show.

### 3. Generate images

On the **Output** tab, write a title and description, set up layout and sorting, pick a design and palette, then press **Generate images**. A preview of every image appears straight away, and changing any setting re-renders it live.

<div align="center">
<img src="assets/panel-generated.png" alt="Generated image preview in the Output tab" width="420">
</div>

### 4. Post it

Press **Save images** (or **Save / share** in Torn PDA), then add the images to your Torn post **in order, part 1 first**. On desktop you can drag them straight into the post editor.

---

## Designs

Fourteen designs, each built for images rather than squeezed into forum HTML. Every one has its own typography and details, three or four curated palettes, and full colour pickers.

<table>
  <tr>
    <td align="center" width="50%" valign="top"><img src="assets/design-glow.png" alt="Neon Box" width="380"><br><b>Neon Box</b><br><sub>Glowing rarity borders and pill prices on a dark grid.</sub></td>
    <td align="center" width="50%" valign="top"><img src="assets/design-banner.png" alt="Gradient Banner" width="380"><br><b>Gradient Banner</b><br><sub>Wide bands that bleed from the item's rarity colour.</sub></td>
  </tr>
  <tr>
    <td align="center" valign="top"><img src="assets/design-split.png" alt="Split Bar" width="380"><br><b>Split Bar</b><br><sub>Condensed headline over a stats bar, split by a rarity line.</sub></td>
    <td align="center" valign="top"><img src="assets/design-stripe.png" alt="Thin Stripe" width="380"><br><b>Thin Stripe</b><br><sub>Dense two-line rows for big inventories.</sub></td>
  </tr>
  <tr>
    <td align="center" valign="top"><img src="assets/design-ledger.png" alt="Classic Ledger" width="380"><br><b>Classic Ledger</b><br><sub>Framed parchment, serif type and dotted price leaders.</sub></td>
    <td align="center" valign="top"><img src="assets/design-minimal.png" alt="Modern Minimalist" width="380"><br><b>Modern Minimalist</b><br><sub>Quiet cards, heavy prices, soft rarity tags.</sub></td>
  </tr>
  <tr>
    <td align="center" valign="top"><img src="assets/design-tactical.png" alt="Military Crate" width="380"><br><b>Military Crate</b><br><sub>Stencil type, riveted plates and hazard stripes.</sub></td>
    <td align="center" valign="top"><img src="assets/design-boutique.png" alt="Luxury Boutique" width="380"><br><b>Luxury Boutique</b><br><sub>Italic serif, gold hairlines and generous space.</sub></td>
  </tr>
  <tr>
    <td align="center" valign="top"><img src="assets/design-slate.png" alt="Slate Card" width="380"><br><b>Slate Card</b><br><sub>Clean dark cards with type badges and bonus chips.</sub></td>
    <td align="center" valign="top"><img src="assets/design-table.png" alt="Compact Table" width="380"><br><b>Compact Table</b><br><sub>Columns that size to your data, for scanning many items.</sub></td>
  </tr>
  <tr>
    <td align="center" valign="top"><img src="assets/design-spec.png" alt="Spec Sheet" width="380"><br><b>Spec Sheet</b><br><sub>Datasheet on a blueprint grid, with stat bars.</sub></td>
    <td align="center" valign="top"><img src="assets/design-swiss.png" alt="Swiss Grid" width="380"><br><b>Swiss Grid</b><br><sub>Strict grid, heavy rules and big index numbers.</sub></td>
  </tr>
  <tr>
    <td align="center" valign="top"><img src="assets/design-receipt.png" alt="Thermal Receipt" width="380"><br><b>Thermal Receipt</b><br><sub>A printed till receipt with total, value and barcode.</sub></td>
    <td align="center" valign="top"><img src="assets/design-brutal.png" alt="Neo Brutalist" width="380"><br><b>Neo Brutalist</b><br><sub>Flat rarity strips, thick ink borders and hard shadows.</sub></td>
  </tr>
</table>

### Make it yours

Each design remembers its own settings:

| Setting | What it changes |
|---|---|
| **Palette** | Three or four curated colour sets per design |
| **Colours** | Pickers for background, cards, text, accent, price and bonus colour (depending on the design) |
| **Corners** | Corner radius, within a range that suits the design |
| **Spacing** | Compact, Regular or Airy |
| **Reset this design** | Back to the design's defaults |

<div align="center">
<img src="assets/palettes-neon-box.png" alt="Neon Box in its Toxic, Synthwave and Ice palettes" width="820">
<br><sub>Neon Box in its three palettes: Toxic, Synthwave and Ice.</sub>
</div>

Text colours are checked against their background automatically, so rarity colours stay readable on light palettes too.

### Image options

| Option | Default | What it does |
|---|---|---|
| Prices | Full | `$250,000,000` or short `$250m` |
| Split at | Medium | Image height before splitting: 1600, 2400 or 3600 px (saved at 2x) |
| Show item images | Off | Adds each item's in-game artwork, loaded from Torn |
| Show date and item count | On | Adds today's date and the item count to the header |
| "Made with ThreadSmith" line | Off | A small credit at the bottom |
| Include item notes | Off | Vault notes appear under each item (Config tab) |
| Show item count in section headers | On | Adds counts to group and section titles (Config tab) |

---

## Auto-split

Long shops are split into several images, so nothing turns into an unreadable sliver on a phone and no file gets huge.

- Splits only happen **between items**. A heading never sits alone at the bottom of an image.
- Each continuation image repeats the shop name and part number at the top, and repeats the current section or group heading marked **(cont.)**.
- Every image ends with **Part 2 of 5 · Continued in part 3**, or **End of list** on the last one.
- Files are named so they sort in order: `my-shop_2026-10-19_part-1-of-5.png`. Lists of 10 or more parts are zero-padded (`part-01-of-12`).

---

## API keys

Create a key in Torn under **Settings → API Keys**. Each sync source needs a different minimum level:

| Sync source | Minimum key level |
|---|---|
| Bazaar | Any key, including **Public** |
| Inventory | **Minimal** or higher |
| Item Market | **Limited** or higher |

Before every sync the script checks your key's level, and Custom keys are checked against their actual selections. If the key is too limited, sync stops with an explanation instead of failing halfway. Torn's API errors (wrong key, paused key, too many requests and so on) are explained in plain language and stay on screen.

```mermaid
flowchart TD
    A["Press Sync"] --> B{"Key level enough<br/>for this source?"}
    B -- "No" --> C["Stops and explains<br/>which level is needed"]
    B -- "Yes" --> D["Fetch listings"]
    D --> E{"Yellow, orange or red<br/>with a bonus?"}
    E -- "No" --> F["Skipped"]
    E -- "Yes" --> G["Added to or refreshed<br/>in the vault"]
```

> [!TIP]
> Your key is stored only in your browser, and is only ever sent to `api.torn.com`.

---

## Torn PDA

RW ThreadSmith works in the [Torn PDA](https://github.com/Manuito83/torn-pda) app.

- **Your PDA key is used automatically** when you have not entered one. If your PDA key lacks access for a sync source, paste a different key into the Sync tab. It is saved and takes priority, and the PDA key is never stored over it.
- **Saving images** opens the phone's share sheet, so you can save to your photos or send the file anywhere.
- The panel is the same as on desktop and follows Torn's theme.

---

## Mug-protection markup

A common Torn tactic is to list an item higher than you really want, so a buy-mugger cannot snipe it cheaply. The downside is that your listing price is no longer the price you want to advertise.

In **Config → Mug Protection Markup**, enter the percentage you pad your listings by. Every price in your images then has that markup removed. It is a true reversal, not a flat subtraction: a 20% markup is divided back out by 1.20.

| You listed | Markup | Images show |
|---|---|---|
| 120M | 20% | 100M |
| 600M | 20% | 500M |
| 36M | 20% | 30M |

- **Set it once.** It applies to every item, including ones synced later.
- **Non-destructive.** Your stored listing price is never changed. Set it back to `0` and prices revert.
- **Rounded to the nearest 1M** so prices stay clean.
- **Manual prices are exempt.** A price you typed yourself is used exactly as written.

---

## The vault

- **Items stay after you delist them.** Mark them `Sold` or `Hidden` instead, and your history is kept.
- **Syncing refreshes prices, not history.** Each sync updates listing prices and adds new items.
- **Listed or Vault.** Each item shows `Listed` (currently in your bazaar or Item Market) or `Vault` (not currently listed).
- **Ranked-war items only.** Anything that is not yellow, orange or red is removed from the vault automatically, including from imported backups.

### Vault filters

| Control | What it does |
|---|---|
| Search | Match item name |
| Bonus | Only items with a specific bonus |
| Rarity | Yellow, Orange or Red |
| Status | Active, Sold or Hidden |
| Sort | Name, Rarity, Type or Status |
| Bulk | Set the filtered items to Active, Sold or Hidden, or remove them |

---

## Layout and sorting

Weapons and armor have separate controls on the Output tab. For example, you can sort weapons by value and armor by rarity.

### Group by

| Group by | Result |
|---|---|
| No grouping | One continuous list |
| Weapon type | Primary, Secondary, Melee, Other |
| Rarity | Yellow, Orange, Red |
| Weapon bonus | One group per bonus, headed by the bonus name |

### Sort by, then by

Each section has a primary **Sort by** and an optional **then by**. The second key only breaks ties the first leaves, and item name is always the final tiebreak.

| Sort option | Available in |
|---|---|
| Value: high to low, low to high | Weapons and armor |
| Name: A to Z, Z to A | Weapons and armor |
| Rarity | Weapons and armor |
| Weapon bonus: A to Z | Weapons and armor |
| Bonus count: most first | Weapons and armor |
| Quality: high to low | Weapons and armor |
| Weapon type | Weapons only |
| Damage: high to low | Weapons only |
| Armor rating: high to low | Armor only |

Unpriced items (shown as Offer) and items missing the sorted stat sink to the bottom.

### Section options

| Setting | What it does |
|---|---|
| Show only | Limit the images to one category |
| Separate armor | Armor gets its own section, grouping, sorting and heading |
| Separate double-bonus gear | Items with two or more bonuses get their own block |
| Include SOLD items | Whether sold items appear at all |
| Move SOLD items to the bottom | Sold items get their own section with a custom heading |

---

## Backup and restore

**Export JSON** on the Sync tab downloads your vault, prices, notes and markup setting. **Import JSON** loads it back on any browser or machine, and merges with your current vault (matching items are overwritten).

- **Clear Prices/Notes** wipes manual prices and notes but keeps the items.
- **Clear Vault** removes everything.

> [!CAUTION]
> Clear Vault cannot be undone. Export a backup first.

---

## FAQ

**Where did the floating button go?**
Since v5 the tool lives in your **My Forums** list on the forum page, as the **RW ThreadSmith** row. Click it to open the panel.

**Nothing shows up after syncing.**
Only ranked-war items are kept: yellow, orange or red rarity with at least one bonus. White items and plain gear are skipped on purpose. Also check that your key's level matches your sync source (see [API keys](#api-keys)); the Sync tab tells you if it doesn't.

**My items are in my inventory, not my bazaar.**
Switch **Config → Sync Source** to **Inventory** (needs a Minimal key or higher). Inventory has no prices, so type them in the Vault. Torn caches inventory for up to an hour, so very recent changes may take a while to appear.

**How do I put the images in my post?**
Save the images, then add them to your Torn post in order, part 1 first. On desktop you can drag them into the editor. In Torn PDA, use the share sheet to save them to your photos first.

**The prices are higher than I want to sell for.**
You pad your listings for mug protection. Set **Mug Protection Markup** in Config to your padding percentage. See [Mug-protection markup](#mug-protection-markup).

**The fonts look plain.**
The designs load their typefaces from Google Fonts. If your userscript manager asked for permission, allow the connection. If fonts cannot load, the images still render with standard system fonts.

**Can I use this on more than one character?**
The vault is stored per browser profile. Use Export and Import to move or separate inventories.

---

## Permissions used

| Permission | Why |
|---|---|
| `GM_setValue` / `GM_getValue` | Store your vault, prices, notes and settings |
| `GM_xmlhttpRequest` | Fallback for network requests when a direct request is blocked |
| `GM_setClipboard` | Clipboard support |
| `@connect api.torn.com` | Your listings and item details |
| `@connect www.torn.com` | Item artwork for images |
| `@connect fonts.googleapis.com`, `fonts.gstatic.com` | Typefaces for the designs |

Nothing is sent anywhere except the Torn API, Torn's own item images and Google Fonts. No data is collected and there are no external servers. Images are rendered entirely in your browser.

---

## Changelog

### v6.2.1

**Changed**
- New anvil icon for the script, matching the one on the forum row. It now shows in Tampermonkey and on Greasy Fork instead of the default placeholder.

### v6.2.0

The first release since v4.8.0. Everything from v4.9 to v6.2 ships together here.

**Added**
- **Image output.** Shops are rendered as high-resolution PNG images instead of HTML. That gets around the forum editor, character limits and broken layouts on phones.
- **14 designs built for images:** Neon Box, Gradient Banner, Split Bar, Thin Stripe, Classic Ledger, Modern Minimalist, Military Crate, Luxury Boutique, Slate Card, Compact Table, Spec Sheet, Swiss Grid, Thermal Receipt and Neo Brutalist.
- **Per-design customization:** curated palettes, colour pickers, corner radius and spacing, remembered separately for each design.
- **Auto-split** into numbered images at clean breaks between items, with continuation headings, part markers and file names that sort in order.
- **Live preview** that re-renders as you change settings, with per-image save buttons.
- **Inventory sync** as a third sync source (Primary, Secondary, Melee and Defensive).
- **Torn PDA support:** automatic use of the PDA key, and saving through the phone's share sheet.
- **Key level check** before every sync, with plain-language explanations for Torn API errors.
- **Item artwork** in images, using the item's real Torn ID stored at sync time.
- Image options: full or short prices, split height, date and item count in the header, optional credit line.
- **Move SOLD items to the bottom** in their own section, with a custom heading.

**Changed**
- **The tool now lives inside the forum page** as a row in your My Forums list, styled with Torn's own theme variables so it follows dark and light mode. The floating launcher and draggable panel are gone.
- Sync source is now a dropdown (Bazaar, Inventory, Item Market) labelled with the key level each needs.
- Network requests use a direct request first and fall back to the userscript manager, so the script works the same in Tampermonkey, Violentmonkey and Torn PDA.
- Sync progress only counts items that actually need an API lookup.
- Sync errors stay on screen instead of disappearing after a moment.
- Custom checkboxes, sliders, colour swatches and scrollbars that match Torn's UI.

**Removed**
- HTML thread output and the HTML-only options (Copy HTML, armor theme).
- The Mobile Table design. Images make mobile-specific layouts unnecessary.

**Fixed**
- **White items are no longer treated as ranked-war items** just because they have a bonus. They are skipped on sync and removed from existing vaults and imports.

### v4.9.0 to v4.11.0 (not released)

- Added a Mobile Table theme for phones (since replaced by image output).
- Themes wrapped name and price onto separate lines on narrow screens.
- Added the option to move SOLD items into their own section at the bottom.
- Tightened header padding and stopped rendering an empty title block.

### v4.8.0

**Changed**
- All Torn API calls now run on API v2. The Bazaar scan moved from `/user/?selections=bazaar` to `/v2/user/bazaar`, and the per-item lookup from `/torn/{id}?selections=itemdetails` to `/v2/torn/{id}/itemdetails`. Item Market sync was already on v2. Vault contents and thread output are unchanged.

### v4.7.0

**Added**
- **Item images**: an optional "Show item images" toggle on the Output tab adds each weapon or armor's in-game image to its card, hotlinked from Torn's own CDN. Works in every theme except Thin Stripe.

### v4.6.0

**Added**
- Two new themes: **Slate Card** and **Spec Sheet**.

**Changed**
- Themes are mobile-friendly and wrap cleanly on phones.
- Classic Ledger redrawn in a clean serif; Military Crate moved to a phone-safe heavy font.
- New-theme headers are centered to match the rest.

**Removed**
- Retro Terminal and Frosted Glass themes (Frosted Glass's blur never rendered in the forum).

### v4.5.0

**Added**
- **Mug Protection Markup** in Config: strip the padding from your listing prices in the output automatically.

**Changed**
- Panel redesigned to match Torn's dark UI, with a launcher button in the bottom-left corner.
- The Vault price field holds only your manual override; blank uses the automatic price. The markup setting is included in Export and Import.

### v4.4.0

**Added**
- Two-level sorting per section (Sort by plus optional then by, with name as the final tiebreak), same-field protection, and a Rarity (reversed) sort.

**Changed**
- Sort comparators rebuilt to chain cleanly.

### v4.3.0

**Added**
- Independent layout and sorting per section; Group by (none, type, rarity, bonus); more sort options; Separate armor with its own grouping, sorting, heading and theme; Separate double-bonus gear; unpriced items sink in value sorts.

### v4.2.0

**Added**
- Item Market sync mode (paginated `/v2/user/itemmarket`, needs a Limited key).

**Changed**
- Config tab reorganised with a Sync Source section.

### v4.1.0

**Added**
- Guide button, viewport-aware width, saved-position validation, drag clamping, SPA navigation guard.

**Changed**
- Raised z-index and contrast across the UI.

**Fixed**
- Frosted Glass Safari prefix, unified note handling, entity-encoded special characters and emoji.

### v4.0.0

**Added**
- Permanent vault, status tracking, tabbed interface, search, filter and sort, bulk actions, per-item notes, live preview, Export and Import, listing-presence tracking, sync progress and summaries, compact mode, include-sold toggle.

**Changed**
- Unified theme system, storage keys renamed from `rw_*` to `rwts_*`, MIT to GPL-3.0, full UI redesign.

**Removed**
- 24-hour cache expiry and auto-clearing prices on sync.

**Fixed**
- Prices and notes persist across syncs; the old cache is migrated automatically.

---

## License

GPL-3.0-or-later · Rowage [3926289] · 2026

Free to use, modify and redistribute under the terms of the GPL-3.0 license.
