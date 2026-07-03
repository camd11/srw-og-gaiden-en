# Super Robot Taisen: Original Generation Gaiden — English Translation Patch

**Version:** 0.2.8 · **Platform:** PlayStation 2 · **Patch format:** xdelta3

This is a fan-made **English translation** of the PlayStation 2 game
*Super Robot Taisen: Original Generation Gaiden* (スーパーロボット大戦OG ジ・インスペクター 外伝 —
JP retail, serial **SLPS-25836**). As far as we can determine (June 2026), no other complete
English translation of this title exists, so this may be the first. (If you find another, great —
please let us know.)

> ## 0.2.8 — community bug round: hardware crash, blank lists, dialogue re-layout (cumulative)
> **0.2.8 fixes every bug reported by the community since 0.2.7** — thank you riohcx, TeddiRiggs,
> Soulgaijin, and yuval4436 for the reports. The headline fixes:
> **the crash on real hardware via OPL at the start of Episode 1 is fixed** (the patch's added
> data sat in memory the PS2's controller/CD drivers write to; emulators masked it — everything
> was relocated to verified-dead space); **the Save/Load slot list and the BGM Select list are
> no longer blank**; and **dialogue has been re-laid-out script-wide**: speaker names are now
> inline (`Name: dialogue...`, the style of Kingcom's OG1 patch and of the JP original), which
> frees a third text row — **no dialogue line anywhere in the game is cut off any more**, and
> the backlog no longer double-draws. Also fixed: the Ally Unit List Movement/Type page garble.
> **Note:** the ELF relocation changes the PCSX2 game CRC to **`1F76B2D9`** — save *states* from
> 0.2.7 won't load; memory-card *saves* carry over fine (re-save once to clean up slot titles
> written by older versions). Everything from 0.2 – 0.2.7 is included; the whole game is
> translated and playable end to end.
>
> It's still a young release with a few **known cosmetic rough edges** (see *Known issues* below), and
> there are surely more we haven't caught. **Please report anything you find** →
> [open an issue](https://github.com/camd11/srw-og-gaiden-en/issues). A screenshot + roughly where it
> happened (stage / menu / battle) is incredibly helpful. Bug reports, suggested wording, and general
> feedback are all welcome.

> **You must supply your own legally-dumped copy of the Japanese disc.** This patch contains only the
> *changed bytes* (the translation) — no copyrighted game data. It is useless without the original ISO.

---

## Screenshots

All captured from the final patched ISO on a fresh New Game — no texture pack, everything is baked into
the patch.

| | |
|---|---|
| **Story dialogue** (inline names + 3 rows, new in 0.2.8) | **Backlog** (clean, new in 0.2.8) |
| ![Dialogue](screenshots/02_dialogue.png) | ![Backlog](screenshots/14_backlog.png) |
| **BGM Select** (un-blanked, new in 0.2.8) | **Save slots** (un-blanked, new in 0.2.8) |
| ![BGM Select](screenshots/15_bgm_select.png) | ![Save slots](screenshots/16_save_slots.png) |
| **Title screen** | **In-battle combat animation** |
| ![Title](screenshots/01_title.png) | ![Combat](screenshots/04_battle_combat.png) |
| **Movement/Type page** (fixed in 0.2.8) | **Unit status screen** |
| ![Movement/Type](screenshots/17_movement_type_fixed.png) | ![Status](screenshots/05_status_unit.png) |
| **Spirit menu** (target line `-Slf / Sgl-`, legend in English) | **Next-episode preview** |
| ![Spirit](screenshots/10_spirit_modeline_EN.png) | ![Next episode](screenshots/18_next_episode.png) |

---

## What's translated

- **Story / event dialogue** — 100% English, in the OG1-English proportional font (Kingcom style:
  inline `Name: dialogue` speaker names, no 「」 brackets).
- **System & menu text** — boot/save prompts, the Intermission UI, unit status & ability screens,
  the battle/map overlays (Unit Stats, HP/EN/Will/SP, OFFENSE/DEFENSE/etc.).
- **In-battle text** — pilot battle barks, support-attack/defense cut-in banners
  (SIMULTANEOUS / ASSIST / EXECUTE ATTACK, SHIELD, SUPPORT ATTACK, SUPPORT DEFENSE), HUD badges.
- **Art / logos** — the title logo, the chapter-intro splash cards ("Episode N" + each chapter title),
  intermission/sortie banners, card-mode menus, and assorted menu sprites redrawn in English.
- **Post-game / omake** content.

Goal of the project: **no Japanese left on screen** during normal play.

---

## Requirements — the exact base ISO

The patch applies to **one specific dump** of the Japanese disc. Verify yours matches before patching:

| | |
|---|---|
| File name (any name is fine) | the JP *OG Gaiden* disc image |
| Serial | **SLPS-25836** |
| Size | **4,666,294,272 bytes** |
| MD5 | `cb7dc4485f46f220c46095c966a3aad0` |
| SHA1 | `2891231bc85603d420c35cda55285d5ecb781f1b` |

If your checksums differ you have a different dump; the patch will refuse to apply (xdelta verifies the
source). Re-dump from your own disc with a tool like ImgBurn or a redump-style dumper.

### The patch file

| | |
|---|---|
| File | `SRW_OG_Gaiden_EN_v0_2_8.xdelta` |
| Size | 3,791,357 bytes |
| MD5 | `e8e94068706c6b00324e64488218320e` |
| SHA1 | `84a061e2335ab458970f3ee5e2ece9d601b8ea36` |

---

## How to apply the patch

You need **xdelta3** (or a GUI front-end for it).

### Easiest — GUI (Windows): Delta Patcher
1. Download **Delta Patcher** (by Phoenix / "DeltaPatcher").
2. *Original file* → your JP `SLPS-25836` ISO.
3. *XDelta patch* → `SRW_OG_Gaiden_EN_v0_2_8.xdelta`.
4. Click **Apply patch**. It writes a new patched ISO next to the original.

### Command line (Windows / macOS / Linux)
```bash
# from a folder containing both the patch and your JP ISO
xdelta3 -d -s "SLPS-25836 (your JP dump).iso" SRW_OG_Gaiden_EN_v0_2_8.xdelta "OG_Gaiden_EN_v0_2_8.iso"
```
- `-d` = decode/apply, `-s` = source (the original JP ISO).
- Install xdelta3: Windows → download the xdelta3 binary; macOS → `brew install xdelta`;
  Debian/Ubuntu → `sudo apt-get install xdelta3`.

### Verify your result
The patched ISO should match:

| | |
|---|---|
| Size | 4,666,294,272 bytes |
| MD5 | `171f7fca4d7192bbd066f1d2925c31c9` |
| SHA1 | `8734d15103bb199f51c3f1b294fd1bbce8355cd7` |

If it matches, the patch applied perfectly.

---

## How to play

- **Emulator (PCSX2):** load the patched ISO. The translation was developed and verified on PCSX2.
  No special settings are required for the text to display in English (it renders straight from the
  disc). The game's CRC after patching is `1F76B2D9` (changed from 0.2.7's `6C5AF6E0`, because 0.2.8
  relocates data inside the boot ELF — so PCSX2 save states made on 0.2.7 will not load on 0.2.8;
  memory-card saves carry over fine).
- **Real hardware:** the patched ISO can be burned / loaded via the usual PS2 backup methods. This is
  a same-size, in-place patch, so it behaves like the original disc on real hardware. **0.2.8
  specifically fixes the Episode-1 crash that 0.2.x had on real hardware via OPL** — if you play on
  console, we'd love confirmation on [issue #1](https://github.com/camd11/srw-og-gaiden-en/issues/1).

---

## Known issues / scope notes

These are minor and cosmetic — normal story + battle play is fully English.

- **Arado's battle quotes intermittently blank or garbled**
  ([issue #4](https://github.com/camd11/srw-og-gaiden-en/issues/4)) — under investigation for the
  next patch. Reports of *which* map/opponent it happens on are very helpful.
- The small **footer/header button-hint labels** (the L1/R1/L2/R2, ◎/△ hints on the unit-status/list
  screens) render as a few garbled pixels, and the per-unit **movement-rank** glyphs in the unit-detail
  overlay are similar. These are drawn through a small UI sprite-font with no Latin glyphs, so they need
  font/art-cell work rather than a text edit — the investigation is well advanced and it's planned for
  a later patch. The button *icons* draw correctly; only the little labels beside them are noise:

  ![Footer hint garble](screenshots/12_remaining_hint_footer.png)

- **Backlog tails on very long lines**: a small number of very long dialogue lines can leave a few
  stale pixels at the end of a backlog row (the dialogue box itself is always complete). Cosmetic,
  and no worse than previous versions.
- A **second copy of the BGM list** used by the intermission Sound menu still has the old blank-row
  issue. The same fix as BGM Select is prepared; it ships once verified on that screen.
- **Save files written by 0.2.7 or older** show a garbled title in the (now-working) save slot list.
  This is baked into the old save data itself — re-saving once on 0.2.8 rewrites it clean. Similarly,
  save files imported from the original JP game can show baked-in Japanese objective text mid-battle;
  start a New Game for the fully-English experience.
- The last two Spirit-legend entries (Sy / Drv) slightly graze the R3 button-hint icon.

Fixed since 0.2: the OPL real-hardware crash, the blank Save/Load slot list, the blank BGM Select
list, script-wide dialogue re-layout ending all box cut-offs and backlog double-draws, and the
Movement/Type page garble (0.2.8); the Ally Unit List placeholder reads `-----` instead of `\\\\\`
(0.2.7), the Spirit target-mode line now reads English (−Slf／Sgl−) and the over-wide status
labels no longer overlap their values (0.2.6), the Spirit-panel bottom legend reads English and the
terrain tile names are English (0.2.5), the per-unit terrain glyphs read Ai/La/Se (0.2.4), the
Spirit-menu crash (0.2.3), the command-menu centering (0.2.2), the full-width objective screen and
splash-title rendering and battle command-menu label fit (0.2.1). See `CHANGELOG.md`.

---

## Reporting issues & feedback

Your playtesting directly shapes the next release. If you hit anything off:

- **Open an issue:** https://github.com/camd11/srw-og-gaiden-en/issues
- Include, if you can: a **screenshot**, **where** it happened (stage / menu / battle screen), and
  whether you were on a **New Game** or an imported save.
- Typos, awkward phrasing, text that runs off the box, untranslated bits, crashes, suggested better
  wording — all of it is welcome.

Fixes will be rolled into the next patch version.

---

## Credits

- **Translation, romhacking, art, testing:** Creamhouse.
- **Built with:** Claude (Anthropic) for reverse-engineering, translation, and tooling; Codex for the
  pixel-art edits.
- **Terminology authority:** Kingcom's English patch of *OG: Original Generations* — the canonical
  English glossary for Original Generation terms, names, and attack names. This project follows it
  wherever the two games overlap.
- Tools in the xdelta / armips lineage made the reinsertion possible.

This is a non-commercial fan project, made for preservation and to let English speakers enjoy a game
that was never localized. **Do not sell this patch or patched discs.** All trademarks and copyrights
belong to their respective owners (Banpresto / Bandai Namco). Distribute the **patch only** — never the
patched ISO or any copyrighted game data.
