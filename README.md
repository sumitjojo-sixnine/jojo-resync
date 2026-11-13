# J O J O Resync

Re-sync any video edit to any song, then finish it with an After Effects-style timeline: SFX layers, keyframed effects, a work area and markers. Drag a song onto your edit and it's matched to your DROP and auto-remixed so its ending lands on your END mark. Exports copy the video untouched, so they're instant and lossless.

## Run it

You need **Python 3.9+** ([python.org](https://www.python.org/downloads/); on Windows, tick "Add to PATH").

- **Windows:** double-click `JOJO Resync.bat`
- **macOS:** double-click `JOJO Resync.command` (first time: right-click → Open)
- **Linux:** `./"JOJO Resync.command"`

The first launch installs its dependencies, which takes about a minute (roughly 400 MB). ffmpeg comes bundled. Your library is stored in `~/JOJOResync`, or `~/ResyncStudio` if you used an earlier version; older projects upgrade automatically.

## The 30-second version

1. Drop your **edit** (a video). It finds the BPM, the **DROP**, the **END** mark and every cut.
2. **Drag a song** from Songs onto the video or the timeline. It's matched to the DROP and **auto-remixed**: it plays from the song's real intro, hits your drop, and its ending (or its last drop) lands on your END mark.
3. Add SFX, effects and keyframes. Set a work area with **B / N**, then **Export** (`⌘/Ctrl+M`).

## After Effects panel (v2, JOJO 4.2)

Work on SFX for any AE comp without leaving your workflow, the way Mocha Pro does:

1. Install `AE Panel/JOJO Resync.jsx` with **File → Scripts → Install ScriptUI Panel…** (AE 2020–2026, Windows & Mac). See `AE Panel/How to install.txt`.
2. Select any comp (or precomp layer) and click **+ Link selected comp**. JOJO opens it as a clean project (video + the comp's own audio, layer cuts, DROP/END comp markers). Add your song and SFX yourself.
3. Press **⤴ Send to AE** (⌘/Ctrl+Shift+A). A **JOJO Mix** layer (song + SFX) with DROP, END and bar markers lands in your comp by itself and updates in place every time you send again.
4. Next time pick the comp in the panel's **Linked comps** list and press **Open in JOJO**: no re-render, all your work is there. **Update preview** re-renders only when you changed the edit in AE.

Projects (with a small MP4 preview and the last two AE mixes) are stored in **Documents → JOJO Resync → Projects**. Settings → After Effects lists every linked comp; Settings → Storage shows what uses space and has **Clear cache** / **Reset JOJO**.

## What's new in 4.4

- **My SFX folders.** SFX tab → *My folders* → ＋ Add folder. Sub-folders become categories (Whoosh, Impact, Riser, Braam, Bass drop, Glitch...). JOJO guesses what each is for from its name - right-click a category to change it. ▶ to listen, drag onto the timeline, or double-click to drop it at the playhead.
- **✨ Auto-SFX.** One click puts sounds from your folders on the edit: a riser that peaks exactly on the DROP, an impact on the hit, a sub drop under it, whooshes on cuts that land on the beat, a braam on the END. Light / Medium / Heavy, pick which kinds, **Shuffle** for other sounds, **Clear** to remove them. They go on their own "Auto ·" layers at the top.
- **Remix versions A / B / C.** Three different musical remixes of the same song - click to listen, keep the best.
- **Best-fit songs.** Songs tab → *Best fit* ranks your library for the loaded edit by tempo (least stretching), drop, length and key (Camelot - songs in matching keys get a boost).
- **Loudness.** Pick TikTok / YouTube / Instagram / Spotify / Loud / Broadcast in the header: exports are set to that LUFS with a true-peak limit. The pill shows the current mix loudness.
- **Templates.** File → *Save setup as template…* keeps your SFX layers and effects; *Templates ▸* puts them on any edit, placed by its DROP / END.
- **.exe + installer + auto-update.** See `build/HOW TO BUILD.txt`.

## What's new in 4.3

- **Song past the end of the video.** Drag the blue handle at the end of the song layer, or use Sync → "After the video ends". The video holds its last frame while the song (and your reverb / echo / SFX) plays on. An END mark on the very end moves with it, so the song's real ending lands there.
- **Musical remix cuts.** The remix now knows which instruments play in every bar (drums or not, loudness, timbre, harmony). It only cuts between parts that sound alike, on 4/8-bar phrase lines, preferring section boundaries, and each cut is a short DJ-style crossfade instead of a hard chop.
- **AE-style graph editor.** Value and Speed graphs, keyframe squares, yellow bezier handles (influence / speed) to shape the curve, Easy Ease / In / Out (F9, Shift+F9, Ctrl+Shift+F9), Hold, Linear, rubber-band select, fit.
- **Export quality.** A normal export copies your video bit-for-bit (4K stays 4K, zero loss). When the video must be re-encoded (work area, song running past the end) it's visually lossless by default; Settings → General → Export quality has a true Lossless option.
- **After Effects.** No more "Not Responding": JOJO is started without AE waiting on it, and previews can render in Media Encoder while you keep working. Projects are grouped by AE project (Documents → JOJO Resync → Projects → <AE project> → <comp>), and a comp you linked before - even after Unlink - gets its own project back.
- **Self-contained projects.** Saving copies the song and SFX into the project's Assets folder.
- **＋ New SFX layer** is now at the top of the timeline.
- **License keys** (see below).

## Sharing JOJO with license keys

Each person gets their own key that only works on their computer:

1. They open JOJO. The activation screen shows their **Machine ID** (e.g. `LRF6-VYRO-SYLC-SYWR`). They send it to you.
2. You run **"Make a key.bat"** in your private *JOJO Keygen* folder (or `python keygen.py make --machine LRF6-VYRO-SYLC-SYWR --name "Rahul" [--days 30]`).
3. Send them the key (`JOJO1.…`). They paste it and press Activate. Done - offline, no server.

`python keygen.py list` shows who you gave keys to. Never share the keygen folder: `jojo_private.key` is what makes keys.

## What's new in 4.2

- **Graph editor.** Click the curve icon next to any keyframed value in Effect Controls (or right-click a property row → Graph editor). Drag keyframes in time and value, double-click to add or remove, and pick Linear / Easy Ease (F9) / Ease In / Ease Out / Hold. Effects on a single clip or song part now show their keyframe rows under the layer in the timeline.
- **Delete anything.** Select a song/edit part (made with ⌘⇧T) and press Delete to remove it (Delete again or ⌘Z brings it back). Delete removes a selected SFX layer, and on the song layer it removes the song from the project.
- **Storage.** Settings → Storage: sizes, Clear cache, Reset JOJO. Previews are small MP4s now.

## What's new in v4

- **Projects, like AE.** Use File ▾ → New / Open / Save (⌘/Ctrl+S, ⌘/Ctrl+Shift+S) to keep everything in a `.jojo` project file. The home screen shows your recent projects, auto-save keeps the file up to date, and opening a project on another library re-imports its files by path.
- **Effects on a single clip.** Select one SFX clip, then click or drag an effect onto it. Only that clip gets it, and reverb or echo tails ring out past the clip's end. Copy effects with ⌘C and paste them onto another clip, song part or layer with ⌘V (right-click works too).
- **Cut the song or the edit audio** with ⌘⇧D or ⌘⇧T. Each part can have its own effects, gain or mute, so you can put Underwater on just the middle of the song.
- **Drag layers up and down** by their names, including the main video and song layers.
- **Essential Sound** (like Premiere Pro): tag each layer as Dialogue, Music, SFX or Ambience. Music then **auto-ducks** under dialogue (and SFX, if you choose), with controls for amount, sensitivity and fades. A yellow line on the lane shows where it ducks.
- **Effects browser** with ★ favourites at the top, collapsible categories and search. Click an effect to add it to whatever is selected.
- **34 moves** (keyframed effects): Into the DROP, On the DROP, At the END, and moves for a single clip or part, such as Reverb out at END, Tape stop at END, Stutter → drop and Reverse swell.
- **12 new effects:** Pitch Shifter, Tape Stop, Stutter, Reverse, Reverse Reverb, Shimmer, Slapback, Doubler, Ring Mod / Robot, Tape Saturation, Exciter and Noise Gate. There are now 30 effects and 27 chain presets.
- **Settings (⚙):** theme, **custom shortcuts** (click one and press the new keys), auto-save, default snap and the home screen.
- **Resizable panels:** drag the gaps between panels. The preview scales when you make the timeline taller.

## Markers

- **DROP** (orange) and **END** (red) are comp markers in the ruler. Drag them, or press **D** / **Shift+D** at the playhead.
- **END** has two modes: *End* (the song's ending lands here) and *End drop* (the song's last drop lands here). JOJO picks one automatically, and you can change it under *Song & Sync → Edit markers*.
- Choose which part of the song goes to END in *Song end → END mark*: Auto, Ending, Drop B/C, or **Shift+click** the song overview.

## Timeline (works like After Effects)

- **Layers:** SFX layers on top, then the Song, the Edit (its own audio, muted by default) and the Master.
- **Layer switches:** **A** (audio on/off), **S** (solo), **L** (lock), a colour label (click to change it), and a twirl to show properties.
- **Properties:** Volume and Pan, plus every effect with its Blend and animatable parameters.
  - Click the **stopwatch** to start keyframing. After that, changing a value adds a keyframe at the playhead.
  - Use the **◀ ◆ ▶** buttons to jump to the previous keyframe, add or remove one at the playhead, or jump to the next.
  - Drag diamonds to move them (Shift-click selects several, Alt-drag changes the value) and press ⌫ to delete.
  - The value numbers are **scrubbable**: drag sideways to change them, or click to type a value.
- **Drag a layer** by its name to reorder it; this works for the song and edit layers too.
- **Header:** a time navigator (drag it, or drag its ends to zoom), the **work area bar** (drag the ends or the middle; double-click to reset), the ruler with seconds and bar numbers, and the playhead.
- **Work area:** playback only plays the part between **B** and **N**, and loops it when Loop is on. Tick **Work area** next to Export to render only that part.
- **The timeline follows the playhead** while it plays, when you jump with the keyboard, and when you scrub past the edge.

### Shortcuts

| Key | Action |
|---|---|
| Space | Play / stop |
| B / N | Work area start / end at the playhead |
| Home / End | Start / end |
| PgUp / PgDn | Previous / next frame (Shift = 10 frames) |
| J / K | Previous / next marker, keyframe or clip edge |
| = / − / \ | Zoom in / zoom out / fit |
| [ / ] | Move the selected clip's start / end to the playhead |
| Alt+[ / Alt+] | Trim the clip's in / out point to the playhead |
| ⌘⇧D or ⌘⇧T | Split the clip, or cut the song / edit audio, at the playhead |
| ⌘D | Duplicate |
| ⌫ | Delete |
| U / L / E | Reveal keyframes / volume / effects |
| D / ⇧D | DROP / END at the playhead |
| S | Place the armed SFX at the playhead (works while playing) |
| , / . | Nudge the song's drop (Shift = a bar) |
| X | Mixer |
| ⌘M | Export |
| ⌘Z | Undo |
| ⌘C / ⌘V | Copy / paste effects |
| ⌘S / ⌘⇧S / ⌘O | Save / Save as / Open project |
| ⌘, | Settings (all shortcuts can be changed here) |

## Effects

You'll find them in **Effects & Presets** (right panel). Drag one onto a timeline layer, a mixer strip or Effect Controls, or double-click it to add it to the selected layer. **Effect Controls** works like AE's: twirl-downs, stopwatches and scrubbable values. A ⧉ button opens the FL-style plugin window with knobs.

- **Audio effects:** Underwater, Reverb, Tempo Delay, EQ, Filter, Compressor, Distortion, Chorus, Flanger, Tremolo, Trance Gate, 8D Auto-pan, Vinyl/Lo-fi, Telephone, Bitcrusher, Stereo Width, Sidechain Pump, Gain.
- **Drop moves:** ready-made keyframes that follow your markers: *Underwater → drop*, *Filter sweep → drop*, *Gate build → drop*, *Echo out at END* and *Duck to silence → drop*.
- **Chain presets:** Underwater, Slowed + reverb, Phonk, Party next door, Old radio, Vinyl, Telephone, 8D audio, Trance gate, Stadium, Dreamy, Hype pump, Punchy SFX, Echo out.

The **Mixer** (`X`) has a fader, pan, mute/solo, meters and 8 insert slots on every channel, plus a limiter on the Master.

## Themes

Click **◐ Theme** for 6 gradient presets (Sunset, Ocean, Aurora, Neon, Ember, Mono), or build your own: three gradient colours, an accent colour (used for the playhead, keyframes and values), glass opacity, blur and glow. Use the 🔊 slider in the transport for preview volume.

## Files

```
resync_studio/engine.py    tempo / drop / END / cut detection, time map, stretching, export
resync_studio/remix.py     bar-level remix planner (drop + END constraints)
resync_studio/effects.py   effects, keyframe curves, presets, limiter
resync_studio/project.py   layers, mixer channels, project render
resync_studio/server.py    local backend + library
resync_studio/static/      the interface
```
