# Motion tokens: your taste as numbers

A token is a named, fixed value that every animation reuses: "entrance curve", "standard duration", "stagger interval". Big design systems use tokens for motion so their products feel like one hand made them. This file does the same for you.

**Fill this from your own After Effects graphs and timelines, not from tutorials.** If a value comes from a tutorial, it's someone else's style. Blanks are fine until Phase 3.

---

## How to read your easing out of After Effects

1. Select a keyframe and press **Cmd/Ctrl + Shift + K** (Keyframe Velocity).
2. Note the **outgoing influence** on the first keyframe and the **incoming influence** on the second. Also check whether the speed is 0.
3. When both speeds are 0, convert to a cubic-bezier, which is the format Remotion and the web use:

```
cubic-bezier( out_influence / 100,  0,  1 − in_influence / 100,  1 )
```

For example, AE's Easy Ease (33.33% / 33.33%) converts to `cubic-bezier(0.333, 0, 0.667, 1)`.

If a curve has overshoot or non-zero speeds, screenshot the Graph Editor (Shift+F3) with the value graph showing and I'll convert it. Overshoot can also be stored as a spring (damping / stiffness / mass).

---

## Frame rate(s)

- Cinematic / personal:
- Client vertical:
- Client 16:9:

## Easing curves (3 at most, because fewer curves make a stronger signature)

| Name | AE influence out → in | cubic-bezier | Used for | Never used for |
|---|---|---|---|---|
| | | | | |
| | | | | |
| | | | | |

## Durations (in frames, at the frame rate above)

| Token | Frames | Used for |
|---|---|---|
| micro | | |
| standard | | |
| emphasis | | |
| scene transition | | |

- Exit duration as a fraction of entrance duration:

## Stagger (the delay between elements in a group)

- Base interval (frames):
- Irregularity: perfectly even, or varied? By how much?
- Order: reading order, importance, outward from center, or something else:

## Overshoot & settle

- Do you use overshoot? Never / sometimes / always:
- Amount (% past the target):
- Frames to settle:
- Things that never overshoot:

## Holds & reading time

- Minimum frames on screen per word:
- Hold after an element lands, before the next move:
- Longest stretch of stillness you'll allow:

## Sync

- What gets synced to sound: cuts? motion hits? text? camera?
- Lead or lag in frames relative to the beat, sound hit or word (e.g. lands 2 frames early):
- What deliberately does **not** sync:

## Motion blur

- On / off:
- Shutter angle:

## Virtual camera

- Constant drift? Speed:
- Push-in amount and duration:
- Number of parallax depth layers:

## Texture

| Treatment | Amount / settings | Always / sometimes / never |
|---|---|---|
| Grain | | |
| Blur / defocus | | |
| Halation / glow | | |
| Vignette | | |
| Chromatic aberration | | |
| Other | | |

## Type behavior

The client supplies the font; you supply how it behaves.

- Scale steps (headline → body → caption):
- Tracking and case:
- Maximum words on screen at once:
- Line-break rule:
- How text enters:
- How text exits:

## Layout

- Grid:
- Safe margins (vertical / 16:9):
- Where text sits by default:

## Color *roles*

The client supplies the colors; you set the rules for using them.

- Maximum colors on screen at once:
- How the accent color is used:
- Background behavior:

---

## Storage format (Phase 3)

Once filled in, this becomes a JSON file that the engine reads directly, for example:

```json
{
  "fps": 30,
  "easing": {
    "entrance": [0.0, 0.0, 0.0, 1.0],
    "exit":     [0.0, 0.0, 0.0, 1.0],
    "move":     [0.0, 0.0, 0.0, 1.0]
  },
  "duration": { "micro": 0, "standard": 0, "emphasis": 0, "scene": 0 },
  "stagger":  { "base": 0, "jitter": 0, "order": "" },
  "sync":     { "leadFrames": 0 }
}
```

(The zeros are placeholders, not suggestions.)
