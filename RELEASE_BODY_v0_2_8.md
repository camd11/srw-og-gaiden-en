English fan-translation of **Super Robot Taisen: Original Generation Gaiden** (PS2, JP serial **SLPS-25836**).

**The whole game is translated and playable end to end.** 0.2.8 is a cumulative release that fixes **every community-reported bug since 0.2.7** — thank you **riohcx**, **TeddiRiggs**, **Soulgaijin**, and **yuval4436** for the reports.

---

## What changed in 0.2.8

- **Crash on real hardware (OPL) at the start of Episode 1 — fixed** ([#1](https://github.com/camd11/srw-og-gaiden-en/issues/1)). All of the patch's added data (font width table, menu helpers, ~300 added strings) turned out to live in a region of the boot ELF that the PS2's controller/CD drivers use as working memory. Emulators masked the collision; real hardware corrupted it at the first controller poll. Every added byte has been relocated into verified-dead space. *If you play on console via OPL, confirmation on the issue would be hugely appreciated.*
- **Save/Load slot list no longer blank** ([#5](https://github.com/camd11/srw-og-gaiden-en/issues/5) + RHDN). Titles, episode numbers, free space — all visible. (Saves written by 0.2.7 or older carry a garbled title *inside the save file*; re-save once on 0.2.8 and it's clean.)
- **BGM Select list no longer blank** ([#2](https://github.com/camd11/srw-og-gaiden-en/issues/2) + RHDN). All 90 track names in full-length English (Kingcom OG1 track-name canon), in BGM Select and the per-unit BGM picker.
- **Dialogue cut-offs and backlog double-draw — fixed script-wide** ([#3](https://github.com/camd11/srw-og-gaiden-en/issues/3)). Speaker names are now **inline** — `Name: dialogue...` — matching Kingcom's OG1 style (and the JP original), which frees a third text row in the dialogue box *and* the backlog. The entire script (~19,500 lines) was re-wrapped: **no dialogue line anywhere in the game is cut off any more**, and the backlog no longer repeats line tails. 21 of ~20,000 lines were very lightly condensed to fit (meaning and character voice preserved).
- **Ally Unit List Movement/Type page — fixed** (RetroGameTalk report). Headers no longer overlap (`Total Mv | Mv Type | Ai La Se`) and the `\` cells are proper dashes.
- Boot slide reads 0.2.8.

> ⚠️ **The PCSX2 game CRC changes from `6C5AF6E0` to `1F76B2D9`** (the ELF relocation). Save **states** made on 0.2.7 will not load on 0.2.8. Memory-card **saves** carry over normally.

Everything from **0.2 – 0.2.7** is included (chapter splashes, Spirit-menu crash fix + legend + target line, terrain names/glyphs, centered command menu, objective screen, unit-list placeholder, battle banners, English boot slide, and the long tail of status-screen fixes).

---

## 📸 Screenshots

All captured from the final patched ISO — no texture pack, everything is baked into the patch.

**The new inline dialogue (three full text rows) · Backlog, clean**

![Dialogue](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/02_dialogue.png)
![Backlog](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/14_backlog.png)

**BGM Select — no longer blank · Save slots — no longer blank**
*(the stray marks on slot rows 1–2 and the "SPECIAL モード" line in this shot are baked into save files written by 0.2.7 and older — re-save once on 0.2.8 and they're clean)*

![BGM Select](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/15_bgm_select.png)
![Save slots](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/16_save_slots.png)

**Movement/Type page — fixed · Spirit menu (still healthy after the relocation)**

![Movement/Type](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/17_movement_type_fixed.png)
![Spirit](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/10_spirit_modeline_EN.png)

**Title screen · Battle**

![Title](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/01_title.png)
![Battle](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/04_battle_combat.png)

### ⚠️ Known remaining issues (all cosmetic; catalogued honestly)

- **Arado's battle quotes** intermittently blank/garbled ([#4](https://github.com/camd11/srw-og-gaiden-en/issues/4)) — under investigation; map/opponent repro details welcome.
- **Footer button-hint labels** still render as pixel noise (a tiny UI sprite-font with no Latin glyphs — needs art-cell work, not text; investigation well advanced).
- **Very long lines** can leave a few stale pixels at the end of a backlog row (box text is always complete; no worse than 0.2.7).
- A **second BGM list copy** used by the intermission Sound menu still has the old blank rows (fix prepared, ships once verified on that screen).
- Spirit-legend `Sy`/`Drv` slightly graze the R3 icon.

Please report anything else via **Issues**.

---

## Get it / apply it

1. Download **`SRW_OG_Gaiden_EN_v0_2_8.xdelta`** below.
2. You must supply your own legally-dumped JP disc (**SLPS-25836**). Verify it first — md5 `cb7dc4485f46f220c46095c966a3aad0`, size 4,666,294,272 bytes.
3. Apply with **xdelta3** (or Delta Patcher on Windows). Full instructions + all checksums are in the repo **README** and in the attached **`CHECKSUMS_v0_2_8.txt`**.

Patched result: md5 `171f7fca4d7192bbd066f1d2925c31c9`, game CRC `1F76B2D9`. **Round-trip verified** — applying the patch to the JP base reproduces the result ISO byte-for-byte.
