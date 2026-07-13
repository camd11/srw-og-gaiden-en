English fan-translation of **Super Robot Taisen: Original Generation Gaiden** (PS2, JP serial **SLPS-25836**).

**The whole game is translated and playable end to end.** 0.2.9 is a cumulative release that fixes the community-reported bugs from the 0.2.8 round — thank you **Soulgaijin**, **JorgeMario-V**, **coconono**, and **riohcx** for the detailed reports and screenshots.

---

## What changed in 0.2.9

- **Backlog (△) crash — fixed** ([#7](https://github.com/camd11/srw-og-gaiden-en/issues/7), [#8](https://github.com/camd11/srw-og-gaiden-en/issues/8)). Opening the backlog during certain dialogues (e.g. Kai and Radha's talk, Stage 4) froze the game — the backlog builder copied long entries with no length cap and could trample its own return address. All three unbounded copies are now bounded. The same fix ends the backlog's **repeated sentences** and the **speaker sprite vanishing** after closing it.
- **Skill Point banner — fixed** ([#8](https://github.com/camd11/srw-og-gaiden-en/issues/8)). The award message was garbled/scattered; it now reads `Skill Point acquired. All pilots +5PP.` cleanly.
- **Story-recap scroll — fixed** ([#8](https://github.com/camd11/srw-og-gaiden-en/issues/8)). The "star wars"-style recap crawl ("New Era year 188…") had lines running off the right edge; the whole crawl is re-wrapped and stays on screen.
- **CONTINUE-screen banner — fixed** ([#8](https://github.com/camd11/srw-og-gaiden-en/issues/8)). The "Continue?" prompt now shows the episode number and title (`OG Gaiden Ch. 1 "Frozen Past"` style) instead of a garbled placeholder.
- **Parts menu descriptions — fixed** ([#8](https://github.com/camd11/srw-og-gaiden-en/issues/8)). Item descriptions in the Upgrade Parts menu (Propellant Tank, Repair Kit, …) now display full English text.
- **VN-scene location banners — fixed** ([#6](https://github.com/camd11/srw-og-gaiden-en/issues/6)). The location caption over story scenes (e.g. `Transport - Hangar`, `Earth Cradle - Interior`, `Italy - Brescia`) garbled after punctuation. Root cause was the banner's own text renderer (a strict 2-byte reader that desynced on our 1-byte space); both banner drawers are patched, so the fix cannot affect any other text.
- In-game episode splash cards (`Episode N` + title) render cleanly.
- Boot slide reads 0.2.9.

> ⚠️ **The PCSX2 game CRC changes from `1F76B2D9` to `DF47D8DA`** (the banner-renderer fix edits the boot ELF). Save **states** made on 0.2.8 will not load on 0.2.9. Memory-card **saves** carry over normally.

### About the OPL / real-hardware freeze ([#1](https://github.com/camd11/srw-og-gaiden-en/issues/1))

**Not claimed fixed in this release.** 0.2.8 fixed the original OPL boot crash; the follow-up freeze at the Stage-2 scrolling intro only reproduces on real hardware via OPL, which we can't test ourselves. A candidate fix exists (it relocates the intro's event data lower on the disc, with **zero** changes to the script) and is posted on the issue as a separate **opt-in test patch**. If you play via OPL, testing it and reporting back is the single most helpful thing you can do — once confirmed, it folds into the next general release.

Everything from **0.2 – 0.2.8** is included (OPL boot-crash fix, save/BGM lists, script-wide inline-name dialogue re-layout, chapter splashes, Spirit-menu fixes, terrain names, battle banners, and the long tail of earlier fixes).

---

## 📸 Screenshots

All captured from the final patched ISO — no texture pack, everything is baked into the patch.

**Backlog — opens clean, no crash · Skill Point banner — fixed**

![Backlog](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/14_backlog.png)
![Skill Point banner](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/20_skill_point_banner.png)

**Story-recap crawl — on-screen · VN location banner — clean**

![Recap crawl](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/19_recap_crawl.png)
![VN location banner](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/23_vn_location_banner.png)

**CONTINUE banner — episode + title · Parts descriptions — restored**

![Continue banner](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/21_continue_banner.png)
![Parts descriptions](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/22_parts_descriptions.png)

**Episode splash · Boot slide**

![Episode splash](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/24_episode_splash.png)
![Boot slide](https://raw.githubusercontent.com/camd11/srw-og-gaiden-en/master/screenshots/09_boot_slide.png)

### ⚠️ Known remaining issues (catalogued honestly)

- **Stage-2 scrolling-intro freeze on real hardware via OPL** ([#1](https://github.com/camd11/srw-og-gaiden-en/issues/1)) — candidate fix awaiting a hardware tester (see above). Emulator play is unaffected.
- **Arado's battle quotes** intermittently blank/garbled ([#4](https://github.com/camd11/srw-og-gaiden-en/issues/4)) — no repro found in the data yet; map/opponent details welcome.
- **Footer button-hint labels** still render as pixel noise (a tiny UI sprite-font with no Latin glyphs — needs art-cell work, not text).
- The CONTINUE dialog shows a small stray `#` after the episode title (pre-existing template control code, visible in the original report too; cosmetic).
- Spirit-legend `Sy`/`Drv` slightly graze the R3 icon.

Please report anything else via **Issues**.

---

## Get it / apply it

1. Download **`SRW_OG_Gaiden_EN_v0_2_9.xdelta`** below.
2. You must supply your own legally-dumped JP disc (**SLPS-25836**). Verify it first — md5 `cb7dc4485f46f220c46095c966a3aad0`, size 4,666,294,272 bytes. (The NTSC-J **Limited Edition** disc is a different master — see [#9](https://github.com/camd11/srw-og-gaiden-en/issues/9).)
3. Apply with **xdelta3** (or Delta Patcher on Windows). Full instructions + all checksums are in the repo **README** and in the attached **`CHECKSUMS_v0_2_9.txt`**.

Patched result: md5 `de91ab6da80135e932a7c58d8dec8271`, game CRC `DF47D8DA`. **Round-trip verified** — applying the patch to the JP base reproduces the result ISO byte-for-byte.
