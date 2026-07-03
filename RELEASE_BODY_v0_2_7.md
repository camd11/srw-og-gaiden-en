English fan-translation of **Super Robot Taisen: Original Generation Gaiden** (PS2, JP serial **SLPS-25836**).

**The whole game is translated and playable end to end.** 0.2.7 is a cumulative release that cleans up the Ally Unit List on top of 0.2.6.

---

## 📸 Screenshots

All captured from the final patched ISO on a fresh New Game — no texture pack, everything is baked into the patch.

### ✅ Translated & working

**Title screen · Story dialogue**

![Title](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/01_title.png)
![Dialogue](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/02_dialogue.png)

**In-battle combat animation · Tactical map**

![Combat](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/04_battle_combat.png)
![Map](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/03_map_movement.png)

**Ally Unit List — sub-line now reads `-----` (was `\\\\\`, NEW in 0.2.7) · Unit status screen**

![Unit list](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/11_unitlist_pilot_dashes.png)
![Status](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/05_status_unit.png)

**Spirit target-mode line `-Slf / Sgl-` · Spirit-menu legend in English**

![Spirit mode line](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/10_spirit_modeline_EN.png)
![Spirit legend](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/08_spirit_legend_EN.png)

**English terrain tile name (`Wastes`) · English boot slide**

![Terrain name](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/06_terrain_name_wastes.png)
![Boot slide](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/09_boot_slide.png)

### ⚠️ Known remaining work (cosmetic only — no readable Japanese)

These are the last rough edges. They are **not text** — they are a UI sprite-font that has no Latin glyphs, so the affected cells render as hatched pixel noise. Fixing them needs an art/font-cell edit (an execution-breakpoint trace to find the glyph table), not a string edit, so they are deferred. No Japanese text is left on screen.

**Footer button-hint labels** — the button icons (START, L3, R3, L1/R1, L2/R2) draw fine, but the little labels beside them render as noise:

![Footer hint garble](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/12_remaining_hint_footer.png)

**Ally Unit List "Movement / Type" page** — the column headers overlap and the per-unit movement-rank separators (`\`) are garbled (the `La` = Land values themselves are correct):

![Movement/Type garble](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/13_remaining_movement_type.png)

Please report anything else you find via **Issues**.

---

## What changed in 0.2.7

- **The Ally Unit List no longer shows `\\\\\` under each unit.** For unnamed mass-produced units (like the prologue's "MP Gespenst Mk-II"), the sub-pilot line was a placeholder of five full-width minus signs (`−−−−−`). Because the English font is ASCII-ordered, the full-width minus mapped to the backslash glyph, so it rendered as `\\\\\`. It now reads `-----`, matching the game's own empty-slot style (e.g. "2  -----"). All eleven full-width-minus runs in the boot ELF's UI string table were converted in place to ASCII dashes.

> ⚠️ **This is the first 0.2.x release to edit the boot ELF**, so the PCSX2 game CRC changes from `6C5AA761` to **`6C5AF6E0`**. Save states made on 0.2.6 (or earlier) will not load on 0.2.7 — start from a memory-card save or a New Game.

Everything from **0.2.6** (Spirit target-mode line `−Slf／Sgl−` + status-label fit), **0.2.5** (Spirit-menu legend + English terrain tile names), **0.2.4** (per-unit Ai / La / Se terrain glyphs), **0.2.3** (Spirit-menu crash fix), **0.2.2** (centered command menu), **0.2.1** (full-width Objective screen), and **0.2** (English chapter splashes, status-screen fixes, battle banners, English boot slide) is included.

## Get it / apply it

1. Download **`SRW_OG_Gaiden_EN_v0_2_7.xdelta`** below.
2. You must supply your own legally-dumped JP disc (**SLPS-25836**). Verify it first — md5 `cb7dc4485f46f220c46095c966a3aad0`, size 4,666,294,272 bytes.
3. Apply with **xdelta3** (or Delta Patcher on Windows). Full instructions + all checksums are in the repo **README** and in the attached **`CHECKSUMS_v0_2_7.txt`**.

Patched result: md5 `ffeb49c99405896d2201bd339b5ca941`, game CRC `6C5AF6E0`. **Round-trip verified** — applying the patch to the JP base reproduces the result ISO byte-for-byte.
