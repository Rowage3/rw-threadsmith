# ⚔ RW ThreadSmith

<div align="center">

**Forum thread generator for Torn RW traders.**
Build beautiful, styled item listings for your bazaar threads in seconds.

[![Version](https://img.shields.io/badge/version-4.1.0-c9a84c?style=flat-square&labelColor=181818)](https://greasyfork.org/scripts/575393)
[![License](https://img.shields.io/badge/license-GPL--3.0-4caf50?style=flat-square&labelColor=181818)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Torn.com-ff6b6b?style=flat-square&labelColor=181818)](https://www.torn.com/forums.php)
[![Free](https://img.shields.io/badge/price-FREE-c9a84c?style=flat-square&labelColor=181818)](#)

[Install](#installation) &nbsp;&middot;&nbsp; [Quickstart](#quickstart) &nbsp;&middot;&nbsp; [Themes](#themes) &nbsp;&middot;&nbsp; [FAQ](#faq)

</div>

---

## What it does

RW ThreadSmith connects to your Torn API, reads your bazaar, and generates fully-styled HTML forum threads you can paste directly into a Torn forum post. Pick a theme, set your prices, hit generate: done.

- **Vault system**: Every item you sync is stored permanently. Items stay in your vault even after you sell or delist them, so you can mark them Sold or Hidden instead of losing history.
- **10 visual themes**: Neon Box, Gradient Banner, Split Bar, Thin Stripe, Classic Ledger, Modern Minimalist, Retro Terminal, Military Crate, Luxury Boutique, Frosted Glass.
- **Live preview**: See exactly what your thread will look like before copying.
- **Per-item notes**: Add a private note to any item (e.g. "negotiable", "reserved for X") that can optionally appear in the generated thread.
- **Bulk actions**: Set entire filtered selections to Active, Sold, or Hidden at once.
- **Export / Import**: Back up your entire vault as JSON. Migrate between browsers or machines.

---

## Installation

You need a userscript manager installed in your browser first.

| Browser | Recommended manager |
|---|---|
| Chrome / Edge / Brave | [Tampermonkey](https://www.tampermonkey.net/) |
| Firefox | [Tampermonkey](https://www.tampermonkey.net/) or [Greasemonkey](https://www.greasespot.net/) |
| Safari | [Tampermonkey](https://www.tampermonkey.net/) |

Once your manager is installed:

1. Click the install link below: your manager will prompt you to confirm.
2. Navigate to any page on `torn.com/forums.php`.
3. The RW ThreadSmith panel appears in the top-right corner.

**[&#x2B07; Install from Greasy Fork](https://greasyfork.org/scripts/575393)**

> The script only runs on `torn.com/forums.php`. It does not run on any other page or site.

---

## Quickstart

### Step 1: Get a Torn API key

Go to **Torn &rarr; Settings &rarr; API Keys** and create a key with at minimum the **Bazaar** permission selected. Copy the key.

### Step 2: Sync your bazaar

Open the **Sync** tab in the panel. Paste your API key and hit **Sync**. The script will scan every item in your bazaar and fetch its stats and bonuses from the Torn API. Items with no bonuses are skipped automatically.

Syncing is rate-limited to protect your API key (~85 requests/minute). A progress bar shows you where it is. You can cancel at any time: items already fetched are saved.

### Step 3: Review your vault

Switch to the **Vault** tab. Every synced item appears here with its rarity color, stats, bonuses, and bazaar listing status.

From here you can:

- **Set status**: `Active` items appear in generated threads. `Sold` items appear with a SOLD badge (toggle in Output settings). `Hidden` items are excluded entirely.
- **Set a manual price**: Override the bazaar price shown in the thread. Accepts formats like `5m`, `1.5b`, `750k`, or a raw number.
- **Add a note**: Enable the notes field in Config, then type anything. Notes are optional and only appear in the thread if you enable "Include item notes in output."
- **Remove**: Permanently delete an item from the vault.

Use the search bar, filters (bonus type, rarity, status), and sort order to navigate large inventories. Bulk actions apply to whatever is currently filtered.

### Step 4: Generate your thread

Switch to the **Output** tab.

1. Enter a thread title and description: these appear as a styled header above your items.
2. Choose how to group items: by **Category** (Primary, Secondary, Melee, Armor, Other) or by **Rarity** (Yellow, Orange, Red, White).
3. Optionally filter to a single category.
4. Pick a **design theme**.
5. Hit **Preview** to see it in a popup, or **Generate &amp; Copy** to copy the HTML directly to your clipboard.
6. Paste into your Torn forum post.

> Torn's forum editor accepts raw HTML. Paste the generated code into the HTML source view of your post.

---

## Vault explained

The vault is the core of RW ThreadSmith. Understanding it saves confusion.

**Items stay after you delist them.** When you remove an item from your bazaar in Torn, it disappears from your bazaar listing: but it stays in your vault. This is intentional. You can mark it `Sold` (it shows with a SOLD badge in threads) or `Hidden` (excluded from all output). This way your thread history is preserved.

**Syncing updates prices, not item data.** Each sync refreshes the bazaar price of items already in the vault. It only makes new API calls for items it has never seen before. This is why syncing gets faster over time.

**The vault never auto-deletes items.** Only you can remove them, via the ✕ button or bulk remove. Clearing your Torn bazaar does not clear the vault.

**Vault-only vs Listed.** In the Vault tab, items show either `Listed` (currently in your Torn bazaar) or `Vault` (not currently listed). This is updated on every sync.

---

## Themes

| Theme | Style |
|---|---|
| **Neon Box** | Rarity-colored glowing border around a dark card. High contrast, bold. |
| **Gradient Banner** | Horizontal gradient strip bleeding from the rarity color. Clean and wide. |
| **Split Bar** | Two-tone card with a rarity underline on the header. Structured. |
| **Thin Stripe** | Dense, compact rows with a thick left-side rarity stripe. Space efficient. |
| **Classic Ledger** | Parchment-toned, serif fonts, dashed borders. Old-school trader aesthetic. |
| **Modern Minimalist** | Solid rarity-colored background cards. Very clean, works best for Yellow/Orange items. |
| **Retro Terminal** | Monospace, green-on-black, fake command line aesthetic. |
| **Military Crate** | Impact font, dark headers, hard edges. Aggressive and readable. |
| **Luxury Boutique** | Italic Georgia serif, gold price text, refined spacing. |
| **Frosted Glass** | Semi-transparent dark cards with blur. Modern UI look. |

All themes use the item's rarity color (Yellow, Orange, Red, White) as the primary accent.

---

## Filters and sorting

### Vault tab filters

| Filter | What it does |
|---|---|
| Search | Text match against item name |
| Bonus type | Show only items with a specific bonus (e.g. Smash, Empower) |
| Rarity | Yellow / Orange / Red / White |
| Status | Active / Sold / Hidden |
| Sort | Name A-Z, Name Z-A, Rarity, Type, Status |

### Output tab filters

| Setting | What it does |
|---|---|
| Group by | Category or Rarity determines section headers |
| Category filter | Restrict output to one weapon/armor type |
| Include SOLD items | Toggle whether Sold items appear in the thread |

---

## Config options

| Option | Default | Description |
|---|---|---|
| Show per-item notes field | Off | Reveals a text input on each vault card for writing notes |
| Compact item cards | Off | Hides stats and bonuses from vault cards to save space |
| Include item notes in output | Off | Notes appear in the generated thread HTML |
| Show item count in section headers | On | Adds "(12)" style count next to each section heading |

---

## Backup and restore

Use **Export JSON** in the Sync tab to download a full backup of your vault, prices, and notes as a `.json` file. Use **Import JSON** to load it back: on any browser, any machine.

Importing merges with your existing vault rather than replacing it. Items with matching UIDs in the import file overwrite their local counterpart.

**Clear Prices/Notes** wipes all manual prices and item notes while keeping vault items intact.

**Clear Vault** removes everything. Export first.

---

## FAQ

**Q: Nothing shows up after syncing.**
A: Check your API key has the Bazaar permission. The script only stores items that have weapon/armor bonuses: standard unmodded items are skipped intentionally since they don't benefit from a styled listing.

**Q: My prices in Torn changed but the thread still shows the old price.**
A: Hit Sync again. Syncing refreshes bazaar prices. If you set a manual price on an item in the Vault tab, that overrides the bazaar price until you clear the price field.

**Q: The panel is off-screen / I can't see it.**
A: Click the **Reset** button in the panel header (if you can see it), or wait for the next page load: the panel position is validated against your viewport on startup. If you used a very small browser window before, it will have been clamped to a valid position on reload.

**Q: Can I use this on multiple characters?**
A: The vault is stored per browser profile using the userscript manager's storage. Different Tampermonkey profiles = separate vaults. Same profile = shared vault. Export/Import is the cleanest way to maintain separate inventories.

**Q: How do I paste the output into a Torn forum post?**
A: Torn's forum editor has an HTML source mode. Click the `<>` or "Source" button in the editor toolbar, then paste the generated HTML there. Do not paste into the visual editor: it will not render correctly.

**Q: The Frosted Glass theme doesn't blur anything.**
A: The blur effect requires a background behind the element to blur. Torn's forum background is white, which makes the glass effect subtle. It renders more dramatically on dark backgrounds. All other visual aspects of the theme still work.

**Q: Can I run this outside forums.php?**
A: The script is restricted to `torn.com/forums.php` by design. That's where you'd create and edit threads. There's no technical reason it couldn't run elsewhere, but the generator output is only useful in the forum editor.

---

## Permissions used

| Permission | Why |
|---|---|
| `GM_xmlhttpRequest` | Fetches item data from the Torn API (bypasses CORS) |
| `GM_setValue` / `GM_getValue` | Stores vault, prices, notes, and settings persistently |
| `GM_setClipboard` | Copies generated HTML to clipboard on Generate |

No data is sent anywhere except to `api.torn.com`. Nothing is collected. No external servers are involved.

---

## Changelog

### v4.1.0
- Panel width now clamps to viewport (`min(450px, 100vw - 24px)`): fixes invisible panel on narrow windows
- Saved position validated against current viewport on load: no more off-screen panel after monitor changes
- Drag boundary clamping: panel cannot be dragged off any edge
- SPA listener guard: prevents duplicate event listeners on Torn's SPA navigation
- Raised z-index to 999999 (panel) and 9999999 (preview) to clear Torn's own modals
- Frosted Glass theme: added `-webkit-backdrop-filter` for full browser support
- Unified `fmtNote()` usage across all themes: `includeNote` flag now consistently respected
- Raised all low-contrast text colors across the panel UI
- Replaced all em-dashes and special characters with HTML entities for encoding safety
- All emoji in tab labels replaced with HTML entities for cross-browser consistency
- Built-in guide button linking to this repository

### v4.0.0
- Vault storage system replacing ephemeral cache
- 10 design themes
- Per-item notes
- Bulk status actions
- Export / Import JSON backup
- Old cache migration to vault format
- Live preview overlay

---

## License

GPL-3.0-or-later &middot; Rowage [3926289] &middot; 2026

Free to use, modify, and redistribute under the terms of the GPL-3.0 license.
