# Next steps: read this first in any new session

Status as of 2026-11-06. This file hands the project from one Claude session to the next, so a session that starts fresh (local or cloud) can pick up exactly where the last one stopped. Update it at the end of every session.

## Where things stand

- **The plan:** `README.md`
- **Round 1 answers, word for word:** `sources/answers-round-1.md`
- **Style bible:** `style-bible.md` (draft v0.1, built from the answers). The user hasn't marked it yet.
- **Work moved to the user's Mac** because cloud sessions limit uploads to 30 MB.

### Decisions so far

- **Tools:** the user edits in DaVinci Resolve on a MacBook. No After Effects.
- **The user directs and Claude builds.** The user can't yet make motion graphics well, but can explain why someone else's graphic works. So:
  1. Claude renders options.
  2. The user picks one and says why.
  3. The chosen values get locked into the motion tokens.
- **Never guess what "punchy" or "smooth" means.** Past attempts went overboard because the numbers were guessed. Calibrate instead.
- **Rendering:**
  - Client videos are finished deliverables, rendered with Remotion.
  - Graphics for the user's own Resolve edits are transparent ProRes 4444 overlays.
- **Direction to explore:** motion graphics that build suspense and awe instead of hype. See `style-bible.md` → "Motion graphics direction".

## Media

Videos go in `media/`, which git ignores, so large files are never pushed. See `media/README.md` for the subfolders. Text notes and explanations go in `sources/` so they're saved to GitHub.

## Queue (in order)

1. **Zoom calibration.** This comes first because it's the user's exact pain point.
   - **Input:** a 10–20 second raw talking-head clip in `media/raw/`.
   - **Render:** versions of that clip with zooms labeled A, B, C… in `media/renders/zoom-calibration/`.
     - Change one thing at a time: zoom amount, duration, or curve.
     - Burn the label into the frame.
     - Never change the frame rate.
   - **The user picks** "punchy", "smooth" and "slow push", and says what's wrong with the ones they rejected.
   - **Record it:**
     - Copy `templates/motion-tokens.md` to `motion-tokens.md`.
     - Fill in the Zooms table with the values and the user's own words.
     - Save the user's reasons verbatim in `sources/`.
2. **Reference breakdowns.**
   - **Input:** 3–5 screen recordings in `media/refs/`.
   - **Claude** measures the how: cut points, frame counts, scale amounts and timing.
   - **The user** explains the why. Record both in `sources/`.
3. **One of the user's best cinematic edits.** Get the render plus its FCPXML in `media/mine/`, then fill in `templates/edit-breakdown.md` with the user.
4. **The user marks `style-bible.md`.** Every line gets ✅, ❌ or ✏️.
5. **Ideas in the user's head.** The user describes one or two roughly, and Claude builds versions.

## Tools on the Mac

- **ffmpeg** is needed for analysis and calibration renders. Check with `ffmpeg -version`. If it's missing, ask the user before installing it (via Homebrew: `brew install ffmpeg`).
- **Node.js** will be needed later for Remotion, but not yet.

## Rules for every session

- Keep `sources/` word for word. Corrections go in the style bible, not in the sources.
- Never commit video files.
- Commit text changes to the branch `claude/editing-style-documentation-a7tb69`, push, and update this file.
