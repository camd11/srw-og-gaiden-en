# Changelog

## 0.2.7 (June 2026) — Ally Unit List placeholder fix (cumulative)

Cumulative on top of 0.2.6. Patch: `SRW_OG_Gaiden_EN_v0_2_7.xdelta` (see `CHECKSUMS.txt`;
round-trip verified). **Note:** unlike 0.2.4–0.2.6, this release edits the boot ELF, so the
PCSX2 game CRC changes from `6C5AA761` to `6C5AF6E0` — save states made on 0.2.6 will not load
on 0.2.7.

- **The Ally Unit List no longer shows `\\\\\` under each unit.** For unnamed mass-produced units
  (e.g. the prologue's "MP Gespenst Mk-II"), the sub-pilot line was a placeholder of five full-width
  minus signs (`−−−−−`). Because the English font is ASCII-ordered, the full-width minus mapped to the
  backslash cell, so it rendered as `\\\\\`. The placeholder (and the other ten full-width-minus runs
  in the boot ELF's UI string table) were converted in place to ASCII dashes, so it now reads `-----`,
  matching the game's own empty-slot style (e.g. "2  -----"). On-screen verified on a fresh New Game.
- Known minor cosmetic (unchanged): the L1/R1/L2/R2 + ◎/△ button-hint labels still render as garbled
  pixels — confirmed this release to be a small UI sprite-font with no Latin glyphs (the in-ROM text
  tables for these labels are dead copies; the live source is sprite/overlay-internal — needs art, not
  a text edit). The unit-list Movement/Type column's single `\` separators and the compact-status
  `Type Land` tail are the same full-width-minus family and remain on the to-do list.

## 0.2.6 (June 2026) — Spirit target-mode line + status-label fit (cumulative)

Cumulative on top of 0.2.5. Patch: `SRW_OG_Gaiden_EN_v0_2_6.xdelta` (see `CHECKSUMS.txt`;
round-trip verified). The boot ELF is unchanged, so the PCSX2 game CRC stays `6C5AA761`; only
`/OL/MPOL.BIN` and `/OL/W1OL.BIN` differ from 0.2.5.

- **The Spirit target-mode line is now English.** Under each spirit's effect, the panel showed the
  spell's target scope as Japanese kanji — `−自／単`. It now reads `−Slf／Sgl−` (the full set:
  Slf = self, Sgl = single, All, Aly = ally, Foe, Sqd = squad, Ptr = partner). Root: the target-type
  strings live in an 8-byte-stride table in `/OL/MPOL.BIN`; the line's renderer advances per full-width
  glyph, so they were re-encoded as full-width Latin abbreviations (pure data edit — no code change, so
  the Spirit-menu crash fix is untouched). On-screen verified on a fresh New Game: the Focus spirit now
  shows `-Slf / Sgl-`, the menu animates, and the Status screen stays English.
- **Over-wide status labels no longer overlap their values.** In the unit-detail overlay the English
  labels were wider than the Japanese originals, so the numbers collided into them ("Support At**1**a**1**k").
  Shortened in place: "Support Attack" → "Sup Atk", "Support Defend" → "Sup Def", "Unit Movement" →
  "Movement".
- Known minor cosmetic (unchanged): the L1/R1/L2/R2 + △ footer button-hint labels and the per-unit
  movement-rank glyphs render as garbled pixels (small UI sprite-font with no Latin glyphs — needs art,
  not a text fix); the last two Spirit-legend entries (Sy / Drv) slightly graze the R3 hint.

## 0.2.5 (June 2026) — Spirit-menu legend + terrain tile names in English (cumulative)

Cumulative on top of 0.2.4. Patch: `SRW_OG_Gaiden_EN_v0_2_5.xdelta` (see `CHECKSUMS.txt`;
round-trip verified). The boot ELF is unchanged from 0.2.4, so the PCSX2 game CRC stays `6C5AA761`;
only `/OL/W1OL.BIN`, `GRAPHIC.BIN`, and `/DATA/MAP.BIN` differ.

- **The Spirit-menu bottom legend is now English.** The reference strip along the bottom of the Spirit
  (精神) panel was a row of 21 single Japanese kanji (熱閃不鉄集必加覚…); it now reads the English spirit
  abbreviations (`VaFlGuIrFoStAcAwMcSnSeLuGaAsRpFsDsSoCoSyDrv`). On-screen verified on a fresh New Game —
  the menu animates (no crash) and the unit Status screen stays fully English.
- **Terrain tile names are now English.** The unit-detail overlay header (above Def%/Eva%/HP Regen%/
  EN Regen%) showed the Japanese terrain name — 荒野 "wasteland", 平地 "flatland", 宇宙空間 "space",
  道路 "road", 軍事基地 "military base", … These are a global terrain table in `MAP.BIN`; all 148 unique
  names are now concise English (SRW terminology, abbreviated to fit the box). In-place data change — no
  code or pointers touched. On-screen verified: a 荒野 tile now reads **"Wastes"**.
- **Boot/credits slide version** bumped to read "Release Version 0.2.5".
- Known minor cosmetic: the last two legend entries (Sy / Drv) slightly overlap the R3 button-hint icon;
  the Spirit panel's `自/単` (Auto/Single) mode line stays Japanese; a few long terrain names are
  abbreviated to fit the on-screen box.

## 0.2.4 (June 2026) — terrain glyphs (cumulative)

Cumulative on top of 0.2.3. Patch: `SRW_OG_Gaiden_EN_v0_2_4.xdelta` (see `CHECKSUMS.txt`;
round-trip verified). The boot-ELF CRC changes `6C5A18B3` → `6C5AA761`.

- **Per-unit terrain glyphs are now English.** A unit's air / land / water terrain compatibility was
  rendered as raw Japanese kanji (空 / 陸 / 水) that the English font turned into garbage — most visible
  in the **Ally Unit List** ("Movement / Type" page), whose terrain column showed a garbled glyph for
  each unit. The column now reads **Ai / La / Se**, matching the unit Status screen's existing terrain
  convention. (In-place text change; no game code touched.)

## 0.2.3 (June 2026) — Spirit-menu crash fix

A stability fix on top of 0.2.2. Patch: `SRW_OG_Gaiden_EN_v0_2_3.xdelta` (see `CHECKSUMS.txt`;
round-trip verified). Game data only; the boot-ELF CRC is unchanged (`6C5A18B3`).

- **The Spirit (精神) command no longer crashes the game.** In every previous English build, choosing
  *Spirit* on a unit's command menu opened a blank panel and froze the game (it worked on the
  unmodified Japanese disc). The translation tool's in-place text edits had corrupted a handful of
  pointer-table entries in one overlay file; the Spirit handler followed a broken pointer and hung.
  Those pointer slots are now restored to their original values while keeping every English label, so
  the Spirit menu works **and** all status/command text stays English. Verified on a fresh New Game.

## 0.2.2 (June 2026) — command-menu centering

A small fix on top of 0.2.1. Patch: `SRW_OG_Gaiden_EN_v0_2_2.xdelta` (see `CHECKSUMS.txt`;
round-trip verified). The boot-ELF CRC changes `4EDB8F5B` → `6C5A18B3`.

- **In-battle command menu now centered.** The map command list (End Turn / Search / Units /
  Objective / Records / System / Save) was drawn with the variable-width font (since 0.2) but still
  *positioned* with the old fixed-width (monospace) centering, so every label sat too far left and
  clipped the panel's left border. Each item is now re-centered for its true variable-width pixel
  width. (ELF-only change; the game data is unchanged.)
- **Note on the 0.2.1 Objective fix:** it applies to objectives loaded fresh from the disc — a New
  Game, or reaching the next stage. Objective text already baked into a mid-stage *suspend save* made
  on an older build keeps the old wrapping until you advance a stage / start a New Game. That's a
  property of the save file, not the patch (a fresh New Game shows the full-width objective).

## 0.2.1 (June 2026) — post-0.2 playtest polish

A small fixes pass on top of 0.2. Patch: `SRW_OG_Gaiden_EN_v0_2_1.xdelta` (see `CHECKSUMS.txt`;
round-trip verified). All three items below were flagged as "known cosmetic" in 0.2 and are now fixed.

- **Chapter splash titles redrawn crisp flat-white** on the black card, replacing the low-contrast,
  banded rendering on the early low-colour cards that looked rough in 0.2.
- **Battle command-menu labels now fit their buttons.** "Battle Report" → "Records" and "Objectives" →
  "Objective" no longer overflow their JP-sized button frames, and the status line "Skill Points" was
  shortened to "Skill Pts" so it no longer collides with its number.
- **In-battle Objective screen now uses the full panel width.** The win/loss/skill conditions previously
  wrapped to only ~1/3 of the wide green panel ("1. Destroy all / enemies."). The cause was hard
  line-breaks (sized for a narrow ~90px width) baked into the objective condition text in `MAP.BIN`.
  Fixed by **MAP pointer-table relocation**: each condition is re-wrapped with full-width spaces and
  moved into unused free space inside its own stage block, with its pointer-table entry repointed. This
  is a pure data change — no runtime code, no crash risk — and keeps `MAP.BIN` byte-for-byte the same
  size. 179 conditions across 41 stage blocks are fixed; the screen now reads e.g.
  "1. Destroy all enemies." / "1. An allied unit is shot down." / "- Meet the victory conditions within /
  3 turns." on full-width lines. (Verified on a fresh boot through the Stage-1 battle.)

## 0.2 (June 2026) — defect-fix pass over 0.1

Fixes found during the 0.1 playtest, validated textures-OFF on the final ISO (no PCSX2 texture pack):

- **Chapter-intro splash screens now in English.** Every chapter title card (e.g. "Frozen Past",
  "Flames Rekindled", … "Ragnarok") and the per-chapter "Episode N" label were pre-rendered Japanese
  bitmaps baked into the disc; all of them are now redrawn in English and baked into the ISO. (These had
  been mis-diagnosed in the 0.1 notes as a save-import artifact — they are real on-disc images.)
- **Menu text spacing.** The Intermission/menu drawer now uses the same variable-width font metric as the
  story dialogue. 0.1 only applied the proportional spacing to dialogue lines, so single-line menu labels
  were spaced with the fixed Japanese cell width and looked uneven; they now kern correctly.
- **Boot caution/intro screen** now shows the English Creamhouse slide instead of Japanese. (The 0.1
  slide was never actually merged into the ISO — a byte-seek splice that silently missed, masked by a
  texture pack. Re-merged with the correct sector-aligned method and proven on-screen.)
- **Battle banners baked into the ISO** (no texture-pack dependence): `ENTRY COMPLETE`, and the in-battle
  status banners `EVADE` / `DISABLED!` / `ATTACK` / `HIT` / `MAX HP` / `B.M COST` (were Japanese).
- **Shuffle Battler banners** (26) translated: `ATK DICE ±N`, `POWER ±N`, `B.M COST n/m` & `×n.n`,
  `NO EVENT CARDS`, `NO COMMAND CARDS`, `NO SUB-UNITS`, `NO ESCAPE`, `ATTACK ONLY`, `CAN'T MOVE!`,
  `OUT OF CONTROL!`, `MAX B.M HALVED`, `NEW LEADER!` (were Japanese).
- **Weapon detail panel:** `Terrain Rating` label no longer overlaps its Air/Land/Sea/Space grades
  (shortened to `Terrain`).
- **Centered system messages** (New Game / Special Menu prompts) no longer overflow the right border —
  the width measure now accounts for English's 1-byte characters, so the text fits and centers.
- **Unit-status screen tabs** (`Unit` / `Mecha` / `Pilot` / `Weapon`) no longer overflow and collide with
  the tab dividers (the English labels were too long for the fixed Japanese tab width).
- **Terrain adaptation ratings** in the unit-status box now render correctly in English. They were garbled
  ("P[Pa P") because the rank letters (A/B/C/S), unit size (S/M/L) and the row's "+"/"=" operators were
  still stored as Japanese full-width characters that the translated font can't draw; these are now plain
  ASCII. The Unit tab reads e.g. `Ai A+A=A`, the Mecha tab `Ai A / La A / Se B / Sp A`.
- **Unit "Type" field** (movement type) now shows English (e.g. `Lnd`) instead of garbled glyphs.
- **Pilot tab field overlaps fixed.** The pilot status page drew several English labels at the fixed
  column positions computed for the shorter Japanese labels, so the value ran back over the label
  ("Mele**1e46**", "Defe**1l38**e", "To Next **500**el", "Air"→"Ai**A**"). The labels are now sized to
  their columns: the six aptitude stats read `Mel / Skl / Mob / Rng / Def / Acc`, the experience line
  reads `Next`, and the pilot's terrain row uses the same `Ai / La / Se / Sp` as the Unit/Mecha tabs.
- **Pilot name spacing.** Two-part pilot names (e.g. `Albero Est`, `Hugo Medio`) were joined with the
  Japanese middle-dot "・", which the English font can't draw and which desynced the following letter
  ("Albero▒EEst"). The join now uses a normal space.
- **Weapon tab detail panel.** Three labels on the weapon status page ran their text back over the value
  in the next column ("W-Gauge **R**q170)", "Terrain **Ra**ting" over its Air/Land grades, "Special
  **E**ffect" over its value). They are now `W-Gauge`, `Terrain`, and `Special`, so each value/grade is
  fully readable.

### Known minor cosmetic items in 0.2 (do not block normal play; targeted for the next patch)

- **Chapter-1 splash looks rough.** The English title cards are rebuilt to follow each Japanese card's
  own brightness/colour ramp; on the low-bit-depth early cards this can band/soften the edges. A simpler
  flat-white render is planned.
- **Objective screen.** Long objective lines wrap early (using only part of the row width), and the
  "Objective" / chapter-title header is a little cramped. The objective drawer still needs the same
  variable-width port the rest of the UI got.
- **Battle (map) menu.** Menu items and the Turn / Funds / Skill-Points readout are positioned slightly
  off; this drawer needs OG1 layout parity.
- **Footer button-hint label.** The action word beside the △ icon on the unit-status/list screens
  (originally 詳細 "Details") still renders as a few garbled pixels — it is drawn through the UI window
  font's unpopulated CJK glyph cells via a render-to-texture path, so a clean fix needs font-glyph work
  out of proportion to a single hint. Deferred.

The earlier "in-battle squished/double text" report turned out to be a non-issue (combat renders
correctly).

## v73 — first public release (June 2026)

Complete English translation of *Super Robot Taisen: Original Generation Gaiden* (SLPS-25836).

Everything below is included in this single release:

- **Story / event dialogue:** 100% translated, rendered in the OG1-English proportional font
  (speaker name above the line, no Japanese quote brackets).
- **System & menu text:** boot/save prompts, Intermission UI, unit status & ability screens, and all
  battle/map overlays in English.
- **In-battle text:** pilot battle barks, the support attack/defense cut-in banners, and HUD badges.
- **Art:** title logo, intermission/sortie banners, card-mode menus, and assorted menu sprites redrawn
  in English.
- **Post-game / omake** content translated.

Patch is size-preserving and applies cleanly to the JP retail dump (see `README.md` for required
checksums). Round-trip verified: applying the patch to the JP base reproduces the released ISO
byte-for-byte.
