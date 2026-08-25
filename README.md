# USFJ SOFA Permit — Flashcards

A single-page flashcard deck for the U.S. Forces Japan SOFA driver's permit test. Flip a card to reveal the answer, mark it as known or needs-review, and the deck keeps cycling the ones you're still shaky on.

**Live:** https://jbarrineau.github.io/sofa-license-flashcards/

## Features

- **181 cards** across four topics — road signs (83), rules of the road (54), licensing & paperwork (24), signals & markings (20).
- **125 keyed visuals**, including embedded road signs and 32 source diagrams/photos in `assets`, so visual questions include the material they ask you to identify.
- **Self-grading loop** — after flipping, mark a card *Got it* or *Review*. Cards you send to review move to the back of the deck instead of disappearing.
- **Progress persists** in `localStorage`, so your known/review marks survive a reload.
- **Session sidebar** with known / review / unseen counts and a mastery percentage for the current topic.
- **Topic filter and shuffle**, plus a reset button to clear all progress.
- **Keyboard driven** — `Space` to flip, `1` for review, `2` for got it, `←`/`→` to move through the deck.

## Running it

The app is static — no build step, dependencies, or server required. Open `index.html` in a browser, or serve the directory:

```sh
python -m http.server 8000
```

Then visit http://localhost:8000. The only network requests are to Google Fonts; sign images are inlined and the remaining source visuals are local assets, so the deck works offline once the page has loaded.

## Question bank

Cards live in the `BANK` array inside `index.html`. Each entry looks like:

```js
{
  "cat": "rules",              // rules | signs | signals | admin
  "q": "…question text…",
  "options": ["…", "…", "…", "…"],
  "a": 2,                      // index of the correct option — shown as the answer
  "why": "…explanation…",
  "img": null,                 // key into IMAGES, or null
  "p": 1                       // study guide page number
}
```

Sign images are keyed in the `IMAGES` object as base64 data URIs. To add a card, append an object to `BANK`; per-topic counts on the topic filter update automatically.

Progress is stored under the `sofa-flashcards-progress` key, mapping each card to `"known"` or `"review"`.

## Related

[sofa-license-quiz](https://github.com/jBarrineau/sofa-license-quiz) — the same question bank as a scored multiple-choice practice test.

## Disclaimer

Study aid only. The Station Safety Center briefing and PMO Pass & Registration are the authority on licensing requirements and Japanese traffic law.
