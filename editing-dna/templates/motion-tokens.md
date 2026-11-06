# Motion tokens: your taste as numbers

A token is a named, fixed value that every animation reuses: "entrance curve", "standard duration", "stagger interval". Big design systems use tokens for motion so their products feel like one hand made them. This file does the same for you.

**Every value here comes from your choices, never from a tutorial or a guess.** If a value comes from a tutorial, it's someone else's style. Blanks are fine until Phase 3.

---

## How we find your numbers: calibration

You don't need to know what an easing curve is. For each token:

1. I render the same clip several ways, labeled A, B, C… Each version changes just one thing: the amount, the speed or the curve.
2. You pick the one that feels right and say what's wrong with the others ("too much", "too late", "feels cheap").
3. The values behind your pick get written here, along with your words. From then on, "punchy zoom" means exactly those numbers and is never guessed again.

Your reasons for rejecting an option are as valuable as your pick.

---

## Zooms (first calibration)

| Name (your word) | Scale from → to (%) | Duration (frames) | Curve | Used for | Never used for | Your words |
|---|---|---|---|---|---|---|
| punchy | | | | | | |
| smooth | | | | | | |
| slow push | | | | | | |

## Frame rate(s)

- Cinematic / personal:
- Client vertical:
- Client 16:9:

## Easing curves (3 at most, because fewer curves make a stronger signature)

| Name | Picked in calibration (test + label) | cubic-bezier | Used for | Never used for |
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
