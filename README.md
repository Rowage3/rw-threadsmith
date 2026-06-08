<div align="center">

# ⚔ RW ThreadSmith

**Forum thread generator for Torn RW traders.**
Build beautiful, styled item listings for your bazaar threads in seconds.

[![Version](https://img.shields.io/badge/version-4.4.0-c9a84c?style=flat-square&labelColor=181818)](https://greasyfork.org/scripts/575393)
[![License](https://img.shields.io/badge/license-GPL--3.0-4caf50?style=flat-square&labelColor=181818)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Torn.com-ff6b6b?style=flat-square&labelColor=181818)](https://www.torn.com/forums.php)
[![Free](https://img.shields.io/badge/price-FREE-c9a84c?style=flat-square&labelColor=181818)](#)

[Install](#installation) &nbsp;&middot;&nbsp; [Quickstart](#quickstart) &nbsp;&middot;&nbsp; [Themes](#themes) &nbsp;&middot;&nbsp; [FAQ](#faq)

</div>

---

## What it does

RW ThreadSmith connects to your Torn API, reads your bazaar or Item Market listings, and generates fully-styled HTML forum threads you can paste directly into a Torn forum post. Pick a theme, set your prices, hit generate: done.

- **Vault system**: Every item you sync is stored permanently. Items stay in your vault even after you sell or delist them, so you can mark them Sold or Hidden instead of losing history.
- **Per-section layout and sorting**: Configure weapons and armor independently. Group each section by type, rarity, or bonus, then order it with a primary and an optional secondary sort. Split armor into its own section and pull double-bonus gear into its own block.
- **10 visual themes**: Neon Box, Gradient Banner, Split Bar, Thin Stripe, Classic Ledger, Modern Minimalist, Retro Terminal, Military Crate, Luxury Boutique, Frosted Glass.
- **Live preview**: See exactly what your thread will look like before copying.
- **Per-item notes**: Add a private note to any item (e.g. "negotiable", "reserved for X") that can optionally appear in the generated thread.
- **Bulk actions**: Set entire filtered selections to Active, Sold, or Hidden at once.
- **Export / Import**: Back up your entire vault as JSON. Migrate between browsers or machines.

---

## Screenshots

<table>
<tr>
<td align="center" width="50%">
<img src="https://i.imgur.com/esiNfs7.png" alt="Sync tab" width="100%"/>
<br/><sub><b>Sync tab</b> - paste your API key, hit Sync, and watch the progress bar as your bazaar or Item Market is scanned.</sub>
</td>
<td align="center" width="50%">
<img src="https://i.imgur.com/7Bi3i8D.png" alt="Vault tab with filters" width="100%"/>
<br/><sub><b>Vault tab</b> - search, filter by bonus type / rarity / status, and manage every item in your collection.</sub>
</td>
</tr>
<tr>
<td align="center" width="50%">
<img src="https://i.imgur.com/jGAeTzR.png" alt="Output tab" width="100%"/>
<br/><sub><b>Output tab</b> - set your thread title, description, per-section grouping and sorting, theme, and filters before generating.</sub>
</td>
<td align="center" width="50%">
<img src="https://i.imgur.com/U5bVITt.png" alt="Live preview" width="100%"/>
<br/><sub><b>Live preview</b> - inspect the generated thread before copying. Upon generating, the code automatically gets on your clipboard, just Ctrl+V.</sub>
</td>
</tr>
<tr>
<td align="center" colspan="2">
<img src="https://i.imgur.com/pI9clPp.png" alt="Config tab" width="50%"/>
<br/><sub><b>Config tab</b> - choose choose sync source, toggle per-item notes, compact cards, note output, and section item counts.</sub>
</td>
</tr>
</table>

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

Go to **Torn &rarr; Settings &rarr; API Keys** and create a key. The permission level you need depends on your sync source:

- **Bazaar sync** (default): **Public Only** permission is sufficient.
- **Item Market sync**: A **Limited** access key is required.

Copy the key.

### Step 2: Sync your items

Open the **Sync** tab in the panel. Paste your API key and hit **Sync**.

By default the script scans your **Bazaar**. If your weapons are listed on the **Item Market** instead, enable **Scan Item Market instead of Bazaar** in the Config tab first.

- **Bazaar mode**: Fetches each item's stats and bonuses from the Torn API individually. Items with no bonuses are skipped automatically.
- **Item Market mode**: Fetches all your Item Market listings in paginated batches. Item stats and bonuses are included directly in the response - no secondary API calls needed, so syncing is faster.

Syncing is rate-limited to protect your API key (~85 requests/minute). A progress bar shows you where it is. You can cancel at any time: items already fetched are saved.

### Step 3: Review your vault

Switch to the **Vault** tab. Every synced item appears here with its rarity color, stats, bonuses, and listing status.

From here you can:

- **Set status**: `Active` items appear in generated threads. `Sold` items appear with a SOLD badge (toggle in Output settings). `Hidden` items are excluded entirely.
- **Set a manual price**: Override the listing price shown in the thread. Accepts formats like `5m`, `1.5b`, `750k`, or a raw number.
- **Add a note**: Enable the notes field in Config, then type anything. Notes are optional and only appear in the thread if you enable "Include item notes in output."
- **Remove**: Permanently delete an item from the vault.

Use the search bar, filters (bonus type, rarity, status), and sort order to navigate large inventories. Bulk actions apply to whatever is currently filtered.

### Step 4: Generate your thread

Switch to the **Output** tab.

1. Enter a thread title and description: these appear as a styled header above your items.
2. Under **Layout & Sorting**, optionally restrict the output to a single category with **Show only**.
3. Configure the **Weapons** section: pick how to **Group by** (no grouping, weapon type, rarity, or weapon bonus), a primary **Sort by**, and an optional **then by** secondary sort.
4. Decide whether to **Separate armor into its own section** at the bottom. When on, the **Armor** section gets its own grouping, sorting, heading text, and an optional theme that can differ from the weapons theme.
5. Optionally **Separate double-bonus gear** into its own block.
6. Pick a **design theme**.
7. Hit **Preview** to see it in a popup, or **Generate &amp; Copy** to copy the HTML directly to your clipboard.
8. Paste into your Torn forum post.

> Torn's forum editor accepts raw HTML. Paste the generated code into the HTML source view of your post.

---

## Vault explained

The vault is the core of RW ThreadSmith. Understanding it saves confusion.

**Items stay after you delist them.** When you remove an item from your bazaar or Item Market in Torn, it disappears from your listing: but it stays in your vault. This is intentional. You can mark it `Sold` (it shows with a SOLD badge in threads) or `Hidden` (excluded from all output). This way your thread history is preserved.

**Syncing updates prices, not item data.** Each sync refreshes the listing price of items already in the vault. It only processes new items it has never seen before. This is why syncing gets faster over time.

**The vault never auto-deletes items.** Only you can remove them, via the ✕ button or bulk remove. Clearing your Torn listings does not clear the vault.

**Vault-only vs Listed.** In the Vault tab, items show either `Listed` (currently in your Torn bazaar or Item Market) or `Vault` (not currently listed). This is updated on every sync.

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

All themes use the item's rarity color (Yellow, Orange, Red, White) as the primary accent. The Armor section can use its own theme or match the weapons theme.

---

## Layout and sorting

The Output tab gives weapons and armor fully independent layout controls, so you can present each section the way that suits it. For example, sort weapons by value while sorting armor by rarity.

### Group by

Each section can be split into headed groups, or left as one flat list.

| Group by | Result |
|---|---|
| No grouping (flat list) | One continuous list, no section headers |
| Weapon type | Primary, Secondary, Melee, Other (weapons section only) |
| Rarity | Yellow, Orange, Red, White |
| Weapon bonus | One group per primary bonus, headed by the bonus name |

### Sort by and then by

Each section has a primary **Sort by** and an optional **then by** secondary sort. The secondary only orders items that the primary leaves tied, and a name sort is always applied last as a final tiebreak. Picking the same field in both slots is blocked, so you cannot create a second level that does nothing.

| Sort option | Available in |
|---|---|
| Value: high to low | Weapons and Armor |
| Value: low to high | Weapons and Armor |
| Name: A to Z | Weapons and Armor |
| Name: Z to A | Weapons and Armor |
| Rarity | Weapons and Armor |
| Rarity (reversed) | Weapons and Armor |
| Weapon bonus: A to Z | Weapons and Armor |
| Bonus count: most first | Weapons and Armor |
| Quality: high to low | Weapons and Armor |
| Weapon type | Weapons only |
| Damage: high to low | Weapons only |
| Armor rating: high to low | Armor only |

Items with no price (shown as Offer) and items missing the stat being sorted on sink to the bottom of that sort instead of mixing into the middle.

### Section options

| Setting | What it does |
|---|---|
| Show only | Restrict the whole output to one category (Primary, Secondary, Melee, Armor, Other) |
| Separate armor into its own section | Moves all armor to its own section at the bottom with its own group, sort, heading, and theme |
| Armor heading | Custom heading text for the armor section |
| Armor theme | Use a different theme for armor, or match the weapons theme |
| Separate double-bonus gear | Pulls items with two or more bonuses into their own block within a section |
| Include SOLD items | Toggle whether Sold items appear in the thread |

---

## Filters and sorting (Vault tab)

| Filter | What it does |
|---|---|
| Search | Text match against item name |
| Bonus type | Show only items with a specific bonus (e.g. Smash, Empower) |
| Rarity | Yellow / Orange / Red / White |
| Status | Active / Sold / Hidden |
| Sort | Name A-Z, Name Z-A, Rarity, Type, Status |

---

## Config options

| Option | Default | Description |
|---|---|---|
| Scan Item Market instead of Bazaar | Off | When enabled, Sync fetches your Item Market listings instead of your Bazaar. Requires a Limited API key. |
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
A: Check your API key and make sure its permission level matches your sync source (Public for Bazaar, Limited for Item Market). The script only stores items that have weapon/armor bonuses: standard unmodded items are skipped intentionally since they don't benefit from a styled listing.

**Q: My weapons are on the Item Market, not the Bazaar.**
A: Enable **Scan Item Market instead of Bazaar** in the Config tab before syncing. You'll also need a Limited access API key - a Public Only key will not have permission to read Item Market listings.

**Q: My prices in Torn changed but the thread still shows the old price.**
A: Hit Sync again. Syncing refreshes listing prices. If you set a manual price on an item in the Vault tab, that overrides the listing price until you clear the price field.

**Q: How do the "Sort by" and "then by" options interact?**
A: The primary "Sort by" decides the order. The "then by" secondary only steps in to break ties the primary left behind, and item name is always the final tiebreak. Order matters: sorting by bonus then value is not the same as value then bonus. You cannot pick the same field in both slots, since the second level would have nothing left to resolve.

**Q: My armor is sorted differently from my weapons. Is that a bug?**
A: No, that is the point. Weapons and armor each have their own Group by, Sort by, and then by. Set them however you like, or turn off "Separate armor into its own section" to fold armor in with the weapon settings.

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

### v4.4.0

**Added:**
- Two-level sorting per section. Each of Weapons and Armor now has a primary **Sort by** plus an optional **then by** secondary sort. The secondary only orders items the primary leaves tied, and item name is always applied as the final tiebreak.
- Same-field protection: once a field is chosen as the primary sort, its matching options are disabled in the "then by" list, so a redundant second level (for example Value high to low then Value low to high) cannot be selected.
- `Rarity (reversed)` added as a sorting option for both Weapons and Armor.

**Changed:**
- Sort comparators rebuilt to be composable, so primary and secondary keys chain cleanly without one swallowing the other.

### v4.3.0

**Added:**
- Independent layout and sorting per section. Weapons and Armor are configured separately, so you can sort weapons by value while sorting armor by rarity.
- **Group by** options: No grouping (flat list), Weapon type, Rarity, or Weapon bonus. Section headers follow your choice.
- Expanded sort options: Value high to low, Value low to high, Name A to Z, Name Z to A, Rarity, Weapon bonus A to Z, Bonus count, Quality, Weapon type, Damage, Armor rating.
- **Separate armor into its own section** at the bottom, with its own grouping, sorting, heading text, and an optional theme override that can differ from the weapons theme.
- **Separate double-bonus gear** into its own block within a section.
- Unpriced items (shown as Offer) and items missing the sorted stat sink to the bottom of value and stat sorts instead of mixing in.

**Changed:**
- The Output tab "Layout" area is now a fuller "Layout & Sorting" panel split into Weapons and Armor controls.
- The old single "Group: Category / Group: Rarity" dropdown is superseded by the per-section Group by selectors. Existing saved grouping carries over on upgrade.

### v4.2.0

**Added:**
- Item Market sync mode: enable "Scan Item Market instead of Bazaar" in the Config tab to fetch listings from `/v2/user/itemmarket` instead of the Bazaar endpoint. Requires a Limited API key.
- Paginated Item Market fetching: all listing pages are retrieved automatically by following the `_metadata.links.next` cursor.
- Item Market sync is faster than Bazaar sync for large inventories: item stats and bonuses are included inline in the listing response, so no secondary per-item API calls are needed.

**Changed:**
- Config tab reorganised: Sync Source section added at the top, above Item Card Display options.
- API key note in Quickstart updated to reflect that Limited access is required for Item Market mode.

### v4.1.0

**Added:**
- Built-in guide button in Config tab linking to the GitHub repository
- Viewport-aware panel width using min() clamp so the panel never overflows on narrow windows
- Saved position validation on startup so the panel cannot load off-screen after a monitor change
- Drag boundary clamping so the panel cannot be pulled off any edge of the screen
- SPA navigation guard preventing duplicate mouse event listeners on Torn page transitions

**Changed:**
- Panel z-index raised to 999999, preview overlay raised to 9999999 to clear Torn's own modals
- All low-contrast text colors raised across the panel UI for better readability
- textFaint raised from #9a9a9a to #aaa, textMain to #e8e8e8, textDim to #c0c0c0
- baz-no label color raised from #777 to #aaa
- Hidden status color raised from #888 to #aaa
- gen-summary color raised from #777 to textDim
- Vault stats empty-state text raised from #777 to textDim
- Generated HTML section header color raised from #888 to #ccc
- Ledger theme statsText raised from #a6927d to #c0a88d
- Glow theme header description color raised from #888 to #ccc

**Fixed:**
- Frosted Glass theme now includes `-webkit-backdrop-filter` for full Safari and older Chromium support
- fmtNote() usage unified across all themes so the includeNote flag is consistently respected in Split and Minimalist themes
- Em-dashes and special characters replaced with HTML entities throughout the panel to prevent encoding issues across browsers
- Emoji in tab labels replaced with HTML entities for cross-browser rendering consistency

### v4.0.0

**Added:**
- Permanent vault storage (items no longer expire after 24 hours)
- Item status tracking (Active, Sold, Hidden) with color-coded badges
- Tabbed interface (Sync, Vault, Output, Config)
- Search, filter, and sort in Vault tab (by name, bonus, rarity, status, type)
- Bulk actions for filtered items (set status, remove)
- Per-item notes field with toggle to include in output
- Live preview modal with copy-from-preview button
- Export/Import JSON for vault, prices, and notes
- Bazaar presence tracking (Listed / Vault badge)
- Sync progress bar and cancel button
- Post-sync summary (new / refreshed / skipped / total)
- Vault stats panel (breakdown by status and listing type)
- Generation summary (items included / hidden / sold / filtered)
- Optional item counts in generated section headers
- Compact card mode for dense item list display
- "Include sold items in output" toggle

**Changed:**
- Theme system refactored (unified palette + item() + header() structure)
- API throttle reduced from 750 ms to 700 ms
- Header settings moved to Output tab
- Storage keys renamed from rw_* to rwts_*
- License changed from MIT to GPL-3.0-or-later
- Full UI redesign with new color scheme and button variants

**Removed:**
- 24-hour cache expiry
- Auto-clear prices on sync

**Fixed:**
- Prices and notes now persist across syncs
- Old v3.9 cache data auto-migrated to new vault system on upgrade

---

## License

GPL-3.0-or-later &middot; Rowage [3926289] &middot; 2026

Free to use, modify, and redistribute under the terms of the GPL-3.0 license.
