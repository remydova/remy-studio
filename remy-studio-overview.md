# remy studio — an overview

*for the person who built this, or anyone who stumbles into this folder and wonders what's going on here.*

---

## what this is

remy studio is a small, private set of tools i made for myself. two html files, no server, no login, no fuss — you just open them in a browser and they work. they exist to help me keep making content without it feeling like a job.

the whole thing runs on claude (the ai) behind the scenes, but the output is written in my voice — lowercase, soft, a little interior. the kind of writing that feels like a letter from a friend who lives quietly and means it.

---

## the tools

### 🌙 quiet notes generator — `newsletter-generator.html`

**what it does**

this one generates a full week of newsletter content in a single session. open it, pick a mood, jot down anything that happened lately (or don't — it works either way), hit generate, and it writes:

- a complete **substack newsletter issue** — subject line, title, opening, two sections, a quote, a prompt for readers, a closing, a ps
- two **substack notes** posts (for wednesday and friday) to keep things warm between issues
- three **pinterest pins** with titles, descriptions, and tags — ready to post

**who it's for**

just me, honestly. it's built around remy dova — the lofi musician persona — so everything that comes out sounds like remy: lowercase, no news, no hot takes, just small and true things about making music at night, miso knocking things over, slow sundays, the way october light hits the window.

**how to use it**

1. open `newsletter-generator.html` in your browser
2. set the issue number (increment it each time — i always forget)
3. pick a mood: reflective, cozy, creative, gentle, hopeful, melancholy
4. optionally write a note in the "this week remy..." box — something small, like *"finished a new track"* or *"miso knocked over her tea"* — this makes the output feel personal
5. hit **generate this week's content** and wait a moment
6. use the tabs to switch between newsletter / substack notes / pinterest pins
7. click **copy for substack**, open substack, paste — the formatting comes through intact
8. copy the notes and pins wherever they need to go

if something feels off, hit **↺ regenerate** — same settings, fresh output.

---

### 🎹 video generator — `video-generator.html`

**what it does**

this one generates short-form video scripts — the kind you'd post on tiktok or instagram reels. it writes the hook, the text overlay cards (in order), and bilingual captions in english and japanese. it also includes step-by-step capcut instructions so i actually know what to do once i open the app.

the whole thing takes about 10 minutes to finish once the script is ready.

**who it's for**

again, just me — but it works for anyone making quiet, slow, introvert-coded video content. it's not made for loud or trend-chasing stuff. it's made for the kind of video where someone sits in a dim room and reads something soft off a screen.

**how to use it**

1. open `video-generator.html` in your browser
2. pick a **video type**:
   - 🌙 affirmation — something gentle and true
   - ☕ introvert tip — small, practical, real
   - 🎹 remy moment — a slice of remy's actual life
   - ✦ mood quote — one feeling, held still
3. pick a **background visual** — remy close-up, remy at desk, remy in rain, or capcut stock options like rain window, candle, coffee steam, autumn leaves
4. pick a **mood** — reflective, cozy, gentle, melancholy, hopeful
5. optionally add context, like *"for people who cancel plans"* or *"about sunday mornings"*
6. hit **generate video script**
7. follow the capcut steps that appear — they tell you exactly which image to use, what effects to apply, and in what order to add the text cards
8. copy the hook, copy the cards, copy the caption (english or japanese)

the image legend at the top reminds you which remy images are which — `remy_video_start_image` for the close-up, `remy-desk` for the full scene, `remy-rain` for moody rainy city shots.

---

## how they work, technically

both tools are self-contained html files — one file, everything inside it, no build step, no npm, no dependencies. open in browser, done.

they call claude through a cloudflare worker proxy (`remy-claude-proxy.gkstutler.workers.dev`) and parse the response as structured json. if the api call fails for any reason, there's fallback content so it never just breaks on you.

---

## the remy dova rules

everything that comes out of these tools follows the same character constraints — and they matter, because consistency is what makes a persona feel real over time:

- always lowercase (except proper nouns)
- never political, never news, never social commentary
- intimate letter voice — not a blog post
- core world: miso (tabby cat), juni (illustrator friend), theo (high school friend), midi keyboard music 9pm–midnight, french press coffee, crochet, ink and watercolor
- muses: studio ghibli, the japanese concept of "ma", snes soundtracks, october light, rain, old bookshops
- tagline: *it's okay to be you.*

---

*remy studio is just two html files and a small quiet dream. open them when you need to make something. close them when you're done.*
