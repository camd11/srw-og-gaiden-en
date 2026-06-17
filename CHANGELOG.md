# Changelog

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
