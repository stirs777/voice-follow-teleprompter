# voice-follow-teleprompter

A teleprompter that follows your voice to move the script.

One HTML file, no build step, no dependencies. It scrolls by listening to you
read, rather than at a fixed speed you have to match.

**Live:** https://stirs777.github.io/voice-follow-teleprompter/

You will need to click the Find Me button a couple of times and grant Chrome microphone access.  

## How the tracking works

It anchors on the most recent word it heard, finds that word in the script
ahead of you, then checks backwards: did the few words before it also match?
Only then does it move the page, easing rather than snapping.

Speech recognition drops and mangles words constantly, so the matcher is
deliberately forgiving — it accepts a shared four-letter stem ("tee" for
"tree"), tolerates a dropped word mid-phrase, and weights words like "the" at
almost nothing so a stray article cannot pull you somewhere else.

Go off-script and it holds still, which is what you want: ad-lib as long as you
like, and it picks you up when you return to the written words. It will follow
you backwards through a restarted sentence, but only on several consecutive
matches, so a repeated "the" can't throw it.

## Setting it up on a tablet

The microphone only works on an **https** address. A file opened directly from
the device's storage (`file://...`) is refused by Chrome, silently. So it has
to be served. Either:

1. **GitHub Pages** — what this repo does. Settings → Pages → Source:
   *Deploy from a branch*, `main`, `/ (root)`. Every push republishes it;
   there is nothing to build.
2. **Netlify Drop** — rename the file to `index.html`, go to
   `app.netlify.com/drop`, and drag it onto the page. A permanent https link in
   about ten seconds, no account needed.

Open the link in Chrome, then **Add to Home screen** so it behaves like an app.
On first run Chrome asks for microphone permission — choose *Allow every time*
so it stops asking.

## Using it with a laptop's built-in webcam

Open **Setup** and tap **Laptop — under the webcam**. That pulls the text into
a narrow column high on the screen and shows only about five lines at a time,
everything else faded out, so your eyes stay close to the lens instead of
travelling down the display. The reading marks move in beside the column for
the same reason.

Three sliders fine-tune it:

- **Lines visible** — fewer lines keeps your eyes in a tighter box. Three is
  very tight; five is comfortable. Set it to 0 to show the whole page.
- **Reading line height** — how far down the screen the line you are reading
  sits. Lower it until it is just under your camera.
- **Text width** — narrower means shorter line sweeps, which reads as less eye
  movement on camera.

**Tablet — full screen** puts it all back.

## The controls

| Button | What it does |
|---|---|
| **Listen** | Starts tracking your voice. Press again to stop. |
| **Find me** | Lost its place? Keep reading, tap this, and it searches the whole script for what it just heard. |
| **Back / Fwd** | Nudge one line. |
| **Script** | Paste, save and load scripts. Also opens `.txt` / `.md` files from the device. |
| **Setup** | Framing presets, lines visible, text size, spacing, width, mirror, fullscreen, keep-screen-on, language, sensitivity. |

**Tap any word** to jump the prompter to it — the fastest recovery there is.

A **Bluetooth page-turner pedal** works: `Space` listen on/off, `down` forward a
line, `up` back a line, `M` mirror, `F` fullscreen. On a laptop, moving the
mouse brings the control bar back; on a tablet, tap anywhere that is not a word.

## Script formatting

- A blank line starts a new paragraph.
- A line starting with `//` becomes a dim stage cue: shown to you, but invisible
  to the tracker, so `// pause, look at camera` will not stall the scroll
  waiting to hear it.

## Known limits

- **Needs internet.** Chrome's speech recognition sends audio to Google's
  servers; there is no offline mode available to a web page. (PromptSmart Pro,
  a paid Android app, does run on-device — worth knowing if you ever film
  somewhere without signal.)
- **Chrome only.** Firefox has no speech recognition. Browser-support tables
  disagree about Chrome on Android, so the Setup panel prints a live check at
  the bottom — look there first if nothing happens.
- Android restarts the speech stream frequently; the app silently restarts it.
  An occasional half-second gap in tracking is that, and is normal.
- Long scripts are fine, but give it a moment to lay out past ~5,000 words.

## If it isn't working

Open **Setup** and read the diagnostic lines at the bottom. They state whether
speech recognition exists, whether the page is on a secure address, and how many
words are loaded. That usually names the problem outright.

## Licence

MIT.
