# KAGUTABA

### The Last Recording

A found-footage horror escape game that runs in your browser. Made for a Halloween hackathon.

A journalist has vanished. His tapes survived. Watch them, find the ritual, and end the curse.

**Play:** https://kagutaba.vercel.app/

**Quick demo:** add `?demo=1` to the link 

> **Trigger warning:** horror, sudden loud sounds and frightening imagery.
> **Gentle Mode** (top bar) turns every scare into a slow fade. The game is fully playable with sound off.
> No webcam, microphone or location is used. No backend, no accounts, no network calls.

---

## How to play

1. Press **Begin the tapes**. This also unlocks audio.
2. On the village map, visit three places: **The Burned House**, **The Archive** and **The Dam Shrine**. Each one holds a clue.
3. Read the **Journal**. It keeps track of what you have found.
4. Work out the order of the four-act ritual and perform it: **Perform the ritual**.
5. Choose carefully. Every wrong attempt costs you tape. When the tape runs out, the recording ends.

Go back to places as often as you like. Revisiting is free, and it is where the game changes.

**Controls:** mouse or touch. Move the pointer (or your finger) to move the flashlight. Tap or drag tiles into the ritual slots. Fullscreen works best on a laptop; on a phone, play in landscape.

---

## What makes it tick

- **A world that lies, clues that don't.** The three essential clues never change. Everything around them does: clue text, the timestamp, the journal's voice, and the figure standing in the room.
- **Revisits change things.** A ghost appears from your second visit to a place and gets bigger every time. By the fourth visit it faces you. The journal slowly switches from "the researcher" to "you".
- **Found-footage look.** VHS grain, scanlines, a running timestamp and a tape counter, all in CSS.
- **Scares are rationed.** There are three, each fires once, and each is placed where the player has relaxed.
- **Sound does a lot of the work.** Room tone everywhere, tape hiss in the house, water at the shrine, voiced clues, and a distant knock.
- **Small touches.** The browser tab changes its title when you leave. If you play between 2 and 6 AM, the journal notices.

---

## Accessibility and safety

- **Gentle Mode** replaces hard cuts with slow, dim fades and lowers the stings. It switches on automatically if your system asks for reduced motion.
- **Sound is optional.** Every voice line has a written version, and the ending has a visual version of every audio beat.
- **No fast flashing.** Nothing flashes more than three times per second.
- A trigger warning is shown before the game starts.

---

## Run locally

```bash
npm install
npm run dev
```

Then open the address Vite prints. To test on a phone on the same Wi-Fi:

```bash
npm run dev -- --host
```

Production build:

```bash
npm run build
npm run preview
```

---

## Fast demo route

Open the game with `?demo=1`. This sets one visit everywhere and pre-discovers the first clues, so the next entry to any place is a revisit.

1. **Archive** → open the film strip → Close.
2. **Journal** → it now says "you".
3. **Burned House** → open the tape.
4. **Dam Shrine** → open the inscription → Close → wait a few seconds.
5. **Dam Shrine** again (third visit) → open the water.
6. **Perform the ritual**, then press EXIT in the ending.

The ghost's glowing eyes only appear from the fourth visit to a place.

<details>
<summary><b>Spoilers: solution, scares and sound map</b></summary>

### The ritual

The four acts, in the correct order: **BOW → CLAP → OFFER → NAME**.
Each wrong attempt adds 2 to the tape counter (out of 10), so the fifth wrong attempt loses.

### Scares

| Scare | Trigger | What happens |
|---|---|---|
| J1 | Archive, 2nd visit, close the film clue | Hard cut to a face, sharp sting, tape counter +1 |
| J2 | Dam Shrine, 3rd visit, open the water clue | Ambience drops to silence, then a larger face and a low sting |
| Loss | Tape counter reaches 10 | Face fills the screen, sharp sting |
| Win | Correct ritual, then EXIT | The ghost comes with you, a breath, a cut to black, the word KAGUTABA, a whisper |

Each scare fires once. In Gentle Mode they become slow fades.

### Sounds

| Sound | Where |
|---|---|
| `room-tone` | Loops on every screen except the start and the endings |
| `tape-hiss` | Loops in the Burned House |
| `water` | Loops in the Dam Shrine |
| `vo-hayashi-e1`, `vo-whisper`, `vo-return` | The tape in the house. The whisper follows the voice, and "You came back." plays from the third visit |
| `vo-okabe-e2` | The film strip in the archive |
| `knock` | Once, shortly after closing the shrine inscription |
| `sting-sharp`, `sting-low` | J1 and the loss, and J2 |
| `fx-breath` | The ending |

</details>

---

## Built with

React 19, Vite, plain JavaScript and CSS. Game state is a single reducer. All content is local data. No libraries beyond React.

```
src/
  App.jsx            screen router, scare and beat logic
  state/gameState.js game state and reducer
  data/              clues, assets, voice cues, credits
  audio/sound.js     ambience, stings and voice playback
  components/        screens and scene pieces
  *.css              layout, VHS effects, typography, depth, retro styling
public/              images, audio and fonts
```

---

## Credits

Inspired by *Noroi: The Curse* (2005), directed by Kōji Shiraishi.
Design and Developed by Hrithika E B and C R Krishna.
Images generated with ChatGPT. Sound effects and voices generated with ElevenLabs.
All art, audio and text in this project are original. No stills or audio from the film are used.
