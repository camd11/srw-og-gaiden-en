# Super Robot Taisen: Original Generation Gaiden — English Translation Patch

**Version:** 0.2.5 · **Platform:** PlayStation 2 · **Patch format:** xdelta3

This is a fan-made **English translation** of the PlayStation 2 game
*Super Robot Taisen: Original Generation Gaiden* (スーパーロボット大戦OG ジ・インスペクター 外伝 —
JP retail, serial **SLPS-25836**). As far as we can determine (June 2026), no other complete
English translation of this title exists, so this may be the first. (If you find another, great —
please let us know.)

> ## 0.2.5 — Spirit-menu legend + terrain tile names in English (cumulative)
> **0.2.5 localizes the last two visible pieces of in-game Japanese text.** The **Spirit (精神) panel's
> bottom reference legend** — a row of 21 single Japanese kanji — now reads the English spirit
> abbreviations (`VaFlGu…SyDrv`). And the **terrain tile names** in the unit-detail overlay are now English
> (荒野 → "Wastes", 平地 → "Flatland", 宇宙空間 → "Space", … 148 terrain types). The boot/credits slide also
> shows the correct version. It builds on **0.2.4** (per-unit air/land/water terrain glyphs now **Ai/La/Se**)
> and **0.2.3** (the Spirit-menu crash fix — choosing *Spirit* used to freeze the game), and carries
> forward everything from 0.2.x: chapter-intro splash screens in English, corrected menu/UI spacing, the
> centered command menu, the full-width objective screen, and the long list of status-screen and
> battle-overlay fixes. The whole game is translated and playable end to end.
>
> It's still a young release with a few **known cosmetic rough edges** (see *Known issues* below), and
> there are surely more we haven't caught. **Please report anything you find** →
> [open an issue](https://github.com/camd11/srw-og-gaiden-en/issues). A screenshot + roughly where it
> happened (stage / menu / battle) is incredibly helpful. Bug reports, suggested wording, and general
> feedback are all welcome.

> **You must supply your own legally-dumped copy of the Japanese disc.** This patch contains only the
> *changed bytes* (the translation) — no copyrighted game data. It is useless without the original ISO.

---

## What's translated

- **Story / event dialogue** — 100% English, in the OG1-English proportional font (Kingcom style:
  speaker name on the line above, no 「」 brackets).
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
| File | `SRW_OG_Gaiden_EN_v0_2_5.xdelta` |
| Size | 3,691,754 bytes |
| MD5 | `966f0346655986fc5f87b2e153c0e0f3` |
| SHA1 | `21d9ad3dcedc89145024e2ada51e3b61583143a2` |

---

## How to apply the patch

You need **xdelta3** (or a GUI front-end for it).

### Easiest — GUI (Windows): Delta Patcher
1. Download **Delta Patcher** (by Phoenix / "DeltaPatcher").
2. *Original file* → your JP `SLPS-25836` ISO.
3. *XDelta patch* → `SRW_OG_Gaiden_EN_v0_2_5.xdelta`.
4. Click **Apply patch**. It writes a new patched ISO next to the original.

### Command line (Windows / macOS / Linux)
```bash
# from a folder containing both the patch and your JP ISO
xdelta3 -d -s "SLPS-25836 (your JP dump).iso" SRW_OG_Gaiden_EN_v0_2_5.xdelta "OG_Gaiden_EN_v0_2_5.iso"
```
- `-d` = decode/apply, `-s` = source (the original JP ISO).
- Install xdelta3: Windows → download the xdelta3 binary; macOS → `brew install xdelta`;
  Debian/Ubuntu → `sudo apt-get install xdelta3`.

### Verify your result
The patched ISO should match:

| | |
|---|---|
| Size | 4,666,294,272 bytes |
| MD5 | `c0e0efcdd9961c158f399b711f9b06f0` |
| SHA1 | `a97991b46bfb94a8b34c54514a94995a903abda4` |

If it matches, the patch applied perfectly.

---

## How to play

- **Emulator (PCSX2):** load the patched ISO. The translation was developed and verified on PCSX2.
  No special settings are required for the text to display in English (it renders straight from the
  disc). The game's CRC after patching is `6C5AA761`.
- **Real hardware:** the patched ISO can be burned / loaded via the usual PS2 backup methods. This is
  a same-size, in-place patch, so it behaves like the original disc on real hardware.

---

## Known issues / scope notes

These are minor and cosmetic — normal story + battle play is fully English. Targeted for the next patch:

- A small **footer button-hint label** (the △ "Details" hint on the unit-status/list screens) shows a
  few garbled pixels — it's a pre-rendered button-hint graphic, not text.
- A two-character mode toggle (自/単) on the Spirit panel, and a handful of deep-menu / developer
  strings, may remain Japanese.
- If you import a **save file made on the original Japanese game** (or a suspend save from an older
  patch build) mid-battle, some objective text baked into that save can show Japanese. Start a
  **New Game** on the patched ISO for the fully-English experience.

Fixed since 0.2: the Spirit-panel bottom legend now reads English and the terrain tile names are now
English (0.2.5), the per-unit terrain glyphs now read Ai/La/Se (0.2.4), the Spirit-menu crash (0.2.3),
the command-menu centering (0.2.2), the full-width objective screen (0.2.1), the splash-title rendering
(0.2.1), and the battle command-menu label fit (0.2.1). See `CHANGELOG.md`.

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
