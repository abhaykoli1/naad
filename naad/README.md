# NAAD — Music App (minimal + premium, glass)

Mood-first music app ka complete concept + working prototype.
Photography-led, frosted-glass chrome, tight grotesk type — aur ek naya USP: **Moments**.

## Files

| File | Kya hai |
|---|---|
| `design-board.html` | **Main design deliverable** — 9 numbered screens + 3 lyrics detail screens + design system + USP + prototype guide |
| `index.html` | **Chalta-phirta app** — saara UI interactive, fonts aur images local (offline chalega) |
| `assets/opt/*.jpg` | 8 photographic covers (generated mock set) |
| `assets/fonts/*.woff2` | Manrope, Instrument Sans, Noto Sans Devanagari — local embed |

## Naya kya hai (is round mein)

### 1. Lyrics box — bada hota hai, animation ke saath
- Player ke neeche **collapsed glass strip** (132px): "abhi kya chal raha hai" + agli line, chhoti waveform ke saath.
- **Swipe up karke drag karein**, ya strip pe **tap** karein → sheet spring animation se full-height ho jaata hai (`cubic-bezier(.32,1.16,.3,1)`).
- Expanded mein: time-synced lines (jo line chal rahi hai woh ivory, baaki dim), **kisi bhi line pe tap = uss point pe jump**, auto-scroll centre.
- Neeche **हिंदी** toggle (real Devanagari translation har line ke neeche) aur **Bigger text**.
- Drag down ya header tap → wapas collapse. (Drag aur tap alag-alag handle hote hain — double-fire bug fix.)

### 2. Font change (Spotify ka Circular nahi)
| Role | Font |
|---|---|
| Display / headings | **Manrope** 650, tracking −0.04em |
| Body / UI | **Instrument Sans** 400–600 |
| Devanagari | **Noto Sans Devanagari** (sirf U+0900–097F range) |

Pehle wala serif headline hata diya — ab poora type ek hi geometric family se, tight tracking ke saath.

### 3. Naya USP — **Moments**
Koi bada music app yaad nahi rakhta ki aapne *kaise* suna. NAAD rakhta hai, **phone pe hi**:
- Discover pe ek **Moments card**: track, time, repeats + ek line ka scene — "you played this three times walking home. It rained for eleven minutes."
- Tags (Rain / Walking / Late), **Replay this moment** (wahi mood ka playlist), Save.
- **Profile → Moments capture** switch: off karte hi card empty-state mein badal jaata hai.
- **Privacy-first:** on-device, kabhi upload nahi, koi social feed nahi.

### 4. Glass effect
Nav bar, mini player, lyrics sheet, moment card, back buttons — sab par:
`blur 26–46px · saturate 150–190% · 1px white border 11–16% · inner top highlight`. Flat grey boxes nahi.

### 5. Black gradient header (no blur, no curve)
- Home / Explore / Library / Inbox ka header ek **solid-black gradient scrim** hai:
  `#0A0A0B 0% → #0A0A0B 34% → 92% → 62% → 24% → 0%` — neeche aate aate **bilkul transparent** ho jaata hai
- **Koi blur nahi, koi tint nahi, koi radius nahi** — sirf black fade
- Scroll karte waqt content us fade ke **peeche se nikalta hai** bina colour change ke
- Header scroll area se **bahar** hai, isliye chips/search/tabs pin rehte hain; `padding-top` auto-measure hota hai taaki content chhupe na
- Greeting line ("Good evening · Aarav") hata di gayi hai — header sirf chips + avatar rakhta hai (107px tall)

### 6. Nav bar (reference ke hisaab se)
- **Docked, full-width bar**: screen ke bottom edge se juda hua (0px gap, koi radius/side margin nahi), upar ek hairline border
- **Transparent + blur**: bar ke peeche se content dikhta hai — `blur(34px) saturate(180%)`, sirf halka tint (alpha 30–58%), koi solid fill nahi
- 5 slots: **Home · Globe (Explore) · ivory ＋ pill · Library · Bell (Inbox)**
- Active slot ke neeche **chhota white dot**; Inbox par **amber unread dot** jo inbox kholte hi clear ho jaata hai
- ＋ hamesha "play something" karta hai (player kholta hai)
- Mini player bar ke upar 20px gap par baithta hai (overlap nahi)

## Prototype chalane ka tarika
`index.html` kholiye (best: Chrome → DevTools → iPhone view).

**Try karein:**
- Welcome → Get started → 2–3 moods select → Continue → home chips aapke moods se badal jaate hain
- Hero / track row / center `+` → player chalta hai, timer badhta hai
- **Lyrics strip pe tap ya swipe-up** → expand; kisi line pe tap → seek; **हिंदी** → translation
- Scratch / drag progress bar, shuffle, repeat, like, next/prev
- ⌄ close → glass mini strip har tab ke upar; uspe tap → player wapas
- **Inbox** (bell icon) — weekly reflection, naya Moment, naye releases
- Profile → Moments capture on/off
- Keyboard: `Space` · `←` `→` · `Esc`

## Design decisions (Spotify se alag)
1. **Mood before genre** — onboarding feeling poochta hai, taste nahi.
2. **Photography only** — dune, water, concrete, window light. Koi gradient/blob nahi.
3. **Glass, not chrome** — frosted layers + hairlines, flat panels nahi.
4. **Ivory, not green** — primary actions warm off-white; amber sirf playback/liked state.
5. **Moments** — listening ki memory, private aur local.

## Notes
- Covers generated mock set hain; production mein label artwork aayega.
- Audio actual play nahi hota — playback engine simulated (timer + progress + queue).
- Not affiliated with Spotify.
