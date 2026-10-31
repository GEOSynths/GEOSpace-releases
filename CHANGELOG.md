# Version history

GEOSpace uses version numbers like 0.9.0: the last number goes up for fixes, the middle one
for new features and the first one for big changes. 1.0.0 is the first public release.
The build number after the version (e.g. 0.9.0 · 6b41ee6) names the exact source it came from.

## 1.0.0 — 2026-10-31
First public release.
- Six effects: BBD-style Chorus (Subtle, Rich, Ensemble, Manual), Phaser, Flanger with
  through-zero, tape/BBD Delay with tempo sync and stereo ping-pong, a 16-line algorithmic
  Reverb with ten models and shimmer, and a 3-band EQ.
- Routing board: any order in series, or two parallel lanes with level and pan.
- Gain In to even out quiet and loud patches, Output, and a hidden look-ahead limiter that
  keeps the output at or below -0.3 dBFS.
- No other companies' product names in GEOSpace: reverb models Vintage Hall, Studio Plate and
  Classic Plate; chorus modes Subtle, Rich and Ensemble; renamed effect and factory presets.
  Only names change: presets and projects load exactly as before.
- 128 factory presets: 35 sounds made on an Oberheim OB-X8 by GEOSynths, 80 variations of
  them (Wide, Haze, Echoes, Swirl, Tight, Dark, Air, Split, Tape, Vast; each level-matched to
  its original) and 12 classic set-ups. Existing installs get the new ones in empty Factory
  slots; nothing you've saved is replaced.
- Banks of 128 presets (one per synth patch), a writable Factory bank, effect presets on the
  back of every card, MIDI learn, and a built-in guide.
- Header: the preset name has a fixed width (long names end in "...", the bank name is
  left out when it doesn't fit), so no button moves; the FX / Routing / Presets tabs sit in
  their own bar, away from Save and Init.
- macOS 11 or later (Apple Silicon and Intel): AU and VST3, signed and notarized installer.
  Windows 10/11 64-bit: VST3 and Standalone installer.

## 0.9.9 — 2026-10-30
- The Routing tab follows the loaded sound: an empty slot, Init or a series preset opens in the
  Series view (their routing is series); a preset that uses the lanes opens in Parallel Lanes.
  Choosing a view by hand is kept until the next preset is loaded.

## 0.9.8 — 2026-10-30
- MIDI Program Change removed, with its channel setting and the MIDI light: presets are
  chosen in GEOSpace (or from the host's preset menu). MIDI learn for the knobs stays.

## 0.9.7 — 2026-10-27
- The Factory bank is writable: its presets are written into your presets folder the first
  time GEOSpace runs and can be edited, saved over, moved and cleared like any other bank.
  **Restore factory presets...** in the Presets tab puts the originals back.
- Loading a factory preset leaves the Output level as it is.
- Windows installer (GEOSpace-x.y.z-Windows-Setup.exe): VST3 and Standalone app, Windows 10/11
  64-bit, built and tested on every build.

## 0.9.6 — 2026-10-27
- The current bank, slot and preset name are lock-protected, so a host saving or restoring the
  project on another thread while a preset loads always stores a complete, correct name.

## 0.9.5 — 2026-10-27
- Robustness (found by new stress tests):
  - No crash when a host sends larger audio blocks than it announced (some offline bounces do).
  - NaN/Inf input from another plug-in is silenced at the input instead of interrupting the sound.
  - Damaged project or preset files can no longer put invalid (NaN or out-of-range) values
    into parameters.
  - The routing never allocates memory on the audio thread.
- Every build now also runs pluginval (strictness 10) on the AU and VST3, validates the
  Intel half of the plug-in, and runs the test and stress suites on macOS.

## 0.9.4 — 2026-10-26
- Init means every effect off: an empty slot (and the Factory "Init") starts with all effects
  switched off, not bypassed, ready for the effect presets or your own settings.
- Init button in the header: clears the current sound to Init in the same slot (asks first if
  there are unsaved changes; the saved preset is only replaced when you Save).
- The < > buttons step through every slot of your banks, empty ones included (they open as
  Init, ready to save into), and ask first if there are unsaved changes.

## 0.9.3 — 2026-10-26
- macOS installer (.pkg): installs the AU and VST3 for all users, with a choice of formats,
  signed with a GEOSynths Developer ID Installer certificate and notarized by Apple.

## 0.9.2 — 2026-10-26
- Permanent plugin identifiers: manufacturer code GEOs, bundle ID com.geosynths.geospace.
  Hosts see this as a new plugin: in Logic projects made with earlier test builds, insert
  GEOSpace again (your presets are unaffected and load as before).
- Signed and notarized with a GEOSynths Developer ID; the download is a drag-to-install DMG.

## 0.9.1 — 2026-10-23
- About panel: link to the GEOSynths website, www.geosynths.com.

## 0.9.0 — 2026-10-23
- MIDI light in the header and in the Presets tab. It flashes on any incoming MIDI; the Presets
  tab also shows the last message and what GEOSpace did with it (slot loaded, slot empty, or
  ignored because Program Change is off or set to another channel).
- About panel: click the GEOSynths logo for the version, host details, a usage guide and this
  version history.
- Program changes are also followed while the plugin is bypassed, so the right preset is ready
  when you switch it back on.
- Header: the sample-rate and tempo readouts are gone (the tempo always comes from the host;
  both now show in the About panel).

## 0.8.0 — 2026-10-22
- Signal-flow audit: the stereo image is kept through every effect, no doubled dry signal,
  no level loss when effects are switched on. Split Dry removed (it doubled the dry signal).
- Input mode defaults to Stereo (a hard-left sound no longer appears on the right).
- Soft silver borders on the effect cards.
- Routing cards fit their names when a section is full; the Presets tab always highlights the
  loaded slot.

## 0.7.0 — 2026-10-22
- Effect presets on the back of every effect card (list button left of the On switch), with
  factory presets for each effect and your own, Mix included.
- Presets work like patches on a synth: a single click loads a slot, an empty slot starts from
  a blank Init sound, drag a preset to move it, a warning before replacing a preset.
- Save button in the header on every tab; `*` after the name while there are unsaved changes.

## 0.6.0 — 2026-10-22
- Output meter with a dBFS legend, peak hold and a steady readout; amber above −6 dBFS, red
  above −1 dBFS or while the limiter works.
- Output goes up to 0 dB (use Gain In to make a quiet sound louder).
- Code cleanup; faster builds.

## 0.5.0 — 2026-10-21
- Auto Gain removed.
- Chorus Dim I / Dim II / Ens III load their Rate, Depth and Width like presets.
- Ping-pong delay bounces in stereo again, with its level matched to the stereo delay.
- Phaser, flanger and delay sit at the same level as the chorus; Mix adds the effect on top.

## 0.4.0 — 2026-10-21
- Gain In at the start of the chain; a hidden look-ahead limiter keeps the output at or below
  −0.3 dBFS.
- EQ is a routing block that can be moved like the other effects.
- New phaser and flanger voicing: stronger, classic sweep, clean feedback, lower CPU.
- Delay: both sides share one modulation, so the echoes stay in time.
- Reverb engine runs at the host rate inside the oversampled graph (about half the CPU).

## 0.3.0 — 2026-10-21
- Redesigned knobs: scale legend, silver rim, value ring.
- Reverb: denser, more transparent tank with less ringing and pitch wobble.

## 0.2.0 — 2026-10-20
- Routing board (Pre, Lane A ∥ Lane B, Post), 3-band EQ, output section and meter.
- Banks of 128 preset slots with MIDI Program Change recall; MIDI learn.

## 0.1.0 — 2026-10-20
- First JUCE build: Chorus, Phaser, Flanger, Delay and Reverb; AU, VST3 and Standalone for macOS.
