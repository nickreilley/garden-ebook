# Editing DNA

This system turns how you edit into something Claude, and every client agent built on Claude, can run without falling back into AI slop.

Start with `00-questions.md`. Everything else in this folder is a template that you fill in, either alone or with me.

---

## 1. Why everything you've tried keeps failing

Ask a model to "make a motion graphic" and you get the average of every motion graphic it has seen, and that average is what slop is. Better prompts get you from a bad average to a good one. They never get you to *your* style, because words like snappy, clean, cinematic and premium mean something different to everyone who types them.

The life in a hand-polished motion graphic comes from keyframe-level decisions. When an AI writes animation from scratch, those are exactly the decisions where it uses the default:

- **Easing:** custom curves, not the default ease-in-out
- **Offset:** elements never all start together, and the delays between them aren't perfectly even
- **Anticipation, overshoot and settle:** or leaving them out on purpose
- **Hierarchy:** one element leads, others follow, and most elements don't move at all
- **Stillness:** holds that let a frame breathe. Motion means something because of the stillness around it
- **Sync:** moves land on the word, the beat or the sound hit, often a frame or two early
- **Motivation:** something causes every move: the voice, the story or the previous move
- **Texture:** grain, blur and drift, so the frame never looks like a flat vector file
- **Sound tied to motion:** designed hits, not a stock whoosh on every transition
- **Phrasing:** on-screen text follows the rhythm of speech, not one word at a time on a metronome

Each of these is a decision. The AI picks the default and you pick something else. **That gap between the default choice and yours is your style**, and it's what this system captures.

## 2. Two changes in approach

**Nothing gets animated from scratch, and you never have to animate.** Every edit is built from a fixed toolkit of signature moves (your text reveal, your transition, your zoom, your number reveal) whose exact values you approved. You're the director: you describe what you want or point at a reference, I build versions, and you pick one and say why. Then, working as the editor, Claude decides which move to use, when, for how long, in what order and in sync with what. Over time each move gets a few "life knobs" (overshoot, how uneven the delays are, hold length) that Claude can turn within limits you set. Film directors work this way with animators: they never touch a keyframe, but they own every decision.

**Your taste gets turned into data.** We capture your style three ways:

1. **Numbers:** easing values, durations, delays between elements, cut lengths and sync offsets, pulled from your real project files rather than described in words.
2. **Reasons:** why you made each choice, in your own words, so Claude can handle situations no rule covers.
3. **Rejections:** what you threw out and why. Taste is mostly what you say no to.

## 3. What we're building

```
┌──────────────────────────────────────────────────────────────┐
│ LAYER 1 · EDITING DNA  (you — identical for every client)    │
│ principles · storytelling rules · motion tokens ·            │
│ signature moves · sound palette · never-list ·               │
│ decision rules · annotated examples                          │
├──────────────────────────────────────────────────────────────┤
│ LAYER 2 · CLIENT BRAND  (swappable)                          │
│ logo · colors · fonts · tone · legal · signature intensity   │
├──────────────────────────────────────────────────────────────┤
│ LAYER 3 · PROJECT BRIEF                                      │
│ script / transcript · footage · goal · platform · deadline   │
└──────────────────────────────────────────────────────────────┘
              │                                    ▲
              ▼                                    │
      ENGINE (renders it) ──► YOUR REVIEW ──► CORRECTION LOG
                                              (updates Layer 1)
```

Your signature has to live in Layer 1: timing, motion personality, sound, composition and transitions. Colors and fonts belong to each client, so they can't be what makes your work recognizable. Keeping the signature in Layer 1 is how someone can spot your edit on two clients with completely different brands.

Layer 1 is packaged as a **Claude skill**: a folder with a `SKILL.md` file and reference files. Every agent you set up for every client loads the same skill, so they all share the same brain. Improve the skill once and every client agent gets better the same day. This isn't fine-tuning, and that's an advantage: you can read it, edit it, keep versions of it, and see exactly why the agent did what it did.

## 4. The engine: where Claude actually makes things

**Motion graphics → Remotion** (a tool where videos are written as React code and rendered to MP4).
- Claude is strongest at writing code, and code renders exactly the same way every time.
- It runs without anyone sitting at editing software, which is what a client agent needs.
- Your signature moves become reusable components with your exact curves built in.
- Audio can be analyzed down to the exact frame of each hit, so motion lands where you would land it.
- Workflow: you describe a move or point at a reference, I build options, you pick. The values you pick get locked in.
- **Client videos:** Remotion renders the whole finished video (footage, graphics, zooms, captions and sound), so agents can deliver without anyone opening editing software.
- **Your own Resolve edits:** graphics render as transparent ProRes 4444 clips that you drop onto the Resolve timeline.
- Check Remotion's license terms once you bill clients for work made with it.

*Later option:* Fusion templates, so graphics stay editable inside Resolve. This isn't the starting point, because client agents need to render without anyone sitting at the software.

**Cinematic and story edits → paper edit + timeline file.**
- Claude works from transcripts and shot logs to build the structure and a cut list.
- It then writes a timeline file (FCPXML) that opens in Resolve as a rough cut, and you finesse it.
- Story structure and picking selects are where Claude helps first. The feel of the final trim stays with you the longest.

**Supporting tools**
- **ffmpeg + scene detection:** pulls cut points, shot lengths and still frames from your finished renders when the project files are gone. It's already available in this environment.
- **Epidemic Sound** (connected to this session): the source for a curated, named sound kit. The kit is what matters: 40 to 80 sounds you always reach for, so the agent never grabs a random whoosh.
- **Sandcastles** (connected): research on hooks and video formats for coming up with ideas.
- **Generative video (Higgsfield, Magnific):** only for raw material such as textures, background plates and b-roll. Never use it for the style itself, because generative models produce averages too.

## 5. The plan

### Phase 1: Capture what already exists (about 2 weeks)
Your storytelling and cinematic instincts already exist; they just aren't written down.
- Pick your 5 best edits. For each one, send:
  - the final render
  - the Resolve timeline export (FCPXML; see `sending-files.md`)
  - a filled-in `templates/edit-breakdown.md`
- Break down 5 to 10 motion graphics you love from other creators. You explain *why* each one works, which is your strength. I measure *how*: frame counts, scale amounts and timing.
- Record 3 sessions of yourself talking while you edit (`templates/think-aloud-protocol.md`). Include one "deliberate default" exercise.
- Fill in `templates/reference-board.md`: 10 videos you love and 10 you hate, with reasons.
- Gather your failed AI attempts and note exactly what was wrong with each.

I'll then pull the numbers, patterns and principles into a first draft of the style bible. You mark every line right, wrong, or "sort of".

### Phase 2: Design the motion signature (about 2 to 3 weeks)
The motion graphics style doesn't exist yet, so we can't extract it. It has to be designed, and **you have to design it.** If I design it, it's my taste, which means the average again. You don't need animation skills for this, only judgment. My job in this phase is to be your hands: I push back on ideas and build the options you choose from.
- **Calibrate the basics first, starting with zooms.** I render the same clip with a range of options (zoom amount, speed and curve). You pick which one is "punchy" and which is "smooth", and those numbers become the permanent definition of each word. This is the fix for zooms that went overboard.
- Describe your motion personality in one sentence, ideally as a physical material (paper, steel, liquid, film stock, magnet). A material comparison settles hundreds of later decisions.
- Set your constraints:
  - 2 to 3 easing curves at most
  - 1 signature transition
  - 1 recurring visual motif
  - 1 texture treatment
  - 1 way text moves
  - 1 signature sound

  Styles become recognizable by repeating a few distinctive decisions, not by doing a lot of different things.
- **Direct 6 to 10 signature moves.** You describe the ideas in your head or point at references, I build versions of each, and you pick and reject. Every choice gets logged with a reason. These moves are the most valuable part of the whole system.

### Phase 3: Write it down and build it (about 2 weeks)
- Fill `templates/motion-tokens.md` with real numbers.
- Rebuild the signature moves as Remotion components.
- Write `templates/style-bible.md`: principles, never-list, decision rules and format playbooks.
- Package everything as the skill.

### Phase 4: The apprentice loop (ongoing)
- Claude edits real projects, you correct them, and every correction goes in `templates/correction-log.md`.
- **Anything you correct twice becomes a rule.**
- **Monthly blind test:** take 5 of your edits and 5 of Claude's, shuffle them, and have someone who knows your work guess which is which. Once their guesses are no better than a coin flip for a format, your style has transferred for that format. This is the only honest way to measure "no difference between my edit and yours".

### Phase 5: Client agents
One brand file per client (`templates/client-brand.md`) plus the skill makes an agent for that client. You keep reviewing that client's work until its format passes the blind test.

## 6. Honest limits
- I see video as a series of still frames, not continuous motion. I can't feel timing by watching the way you do, so I need numbers from project files and your own words. That's why the capture phase relies on project data and narration rather than just finished renders.
- No shortcut skips Phase 2. If you don't define the style, any AI will fill the gap with the average.
- Early outputs will still need your hands. The blind test tells us when they stop needing them, so we don't have to guess.

---

## Folder map
```
editing-dna/
  README.md                       this plan
  00-questions.md                 answer these first
  style-bible.md                  the live style bible (draft v0.1, needs your marks)
  sending-files.md                how to export from Resolve under 30 MB
  sources/                        your raw answers and recordings, unedited
  templates/
    edit-breakdown.md             the "why" behind one finished edit
    think-aloud-protocol.md       recording yourself while you edit
    reference-board.md            loves, hates and reasons
    motion-tokens.md              your taste as numbers
    style-bible.md                principles, signature moves, never-list
    correction-log.md             the apprentice loop + blind tests
    client-brand.md               what each client owns vs. what you own
```
