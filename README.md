# voice-follow-teleprompter
A teleprompter that follows your voice to move the script

(C) Voice-Follow Teleprompter — how to use it
A single-file web teleprompter that scrolls by listening to you read, rather than at a fixed speed. Built 2026-10-20 at Sterling's request.

File: (C) Voice-Follow Teleprompter.html

Getting it onto the Android tablet
The microphone will only work on an https address. A file opened directly from the tablet's storage (file://...) will be refused by Chrome, silently. So it has to be served. Two ways, easiest first:

Netlify Drop — rename the file to index.html, go to app.netlify.com/drop on any computer, drag the file onto the page. You get a permanent https link in about ten seconds. No account needed to start. Open that link in Chrome on the tablet, then Add to Home screen so it behaves like an app.
GitHub Pages — put the file as index.html in a public repo (a new one, not this vault, which should stay private) and turn Pages on in the repo settings. Also free and permanent.
First run: Chrome will ask for microphone permission. Say yes, and choose "Allow every time" so it stops asking.

Using it on the laptop with the built-in webcam
Open Setup and tap Laptop — under the webcam. That pulls the text into a narrow column high on the screen and shows only about five lines at a time, everything else faded out, so your eyes stay close to the lens instead of travelling down the display. The two amber marks now sit beside the column rather than at the screen edges, for the same reason.

From there, three sliders do the fine-tuning:

Lines visible — fewer lines keeps your eyes in a tighter box. Three is very tight; five is comfortable. Set it to 0 to see the whole page again.
Reading line height — how far down the screen the line you are reading sits. Lower it until it is just under your camera.
Text width — narrower means shorter line sweeps, which reads as less eye movement on camera.
Tap Tablet — full screen to put everything back.

Getting it to run on the laptop: the microphone rule is the same here — it needs an https address. Try double-clicking the file first; open Setup and read the diagnostic at the bottom, which states whether the page is on a secure address. If the microphone is refused, open the hosted link instead. It is the same app, and it works on any device with Chrome.

The controls
Button	What it does
Listen	Starts tracking your voice. Press again to stop.
Find me	Lost its place? Keep reading, tap this, and it searches the whole script for what it just heard.
Back / Fwd	Nudge one line.
Script	Paste, save, and load scripts. Also opens .txt / .md files straight from the tablet.
Setup	Framing presets, lines visible, text size, spacing, width, mirror, fullscreen, keep-screen-on, language, sensitivity.
Tap any word to jump the prompter to it — the fastest recovery there is.

A Bluetooth page-turner pedal works: Space = listen on/off, down = forward a line, up = back a line, M = mirror, F = fullscreen.

Script formatting
A blank line starts a new paragraph.
A line starting with // becomes a dim stage cue — shown to you, but invisible to the voice tracker, so // pause, look at camera won't stall the scroll.
What it does when you go off-script
It holds still. That is deliberate — it is how the commercial voice prompters behave. Ad-lib as long as you like; when you return to the written words it picks you back up. It will also follow you backwards if you restart a sentence, but only when several words in a row match, so a repeated "the" can't throw it.

Known limits
Needs internet. Chrome's speech recognition sends audio to Google's servers. There is no offline mode in a web page. (PromptSmart Pro, the paid Android app, does run on-device — worth knowing if you ever film somewhere without signal.)
Chrome only. Firefox for Android has no speech recognition at all. Browser-support tables disagree about Chrome on Android, so the Setup panel prints a live check at the bottom — look there first if nothing happens.
Android restarts the speech stream frequently; the app silently restarts it. A half-second gap in tracking now and then is that, and is normal.
Long scripts are fine, but give it a moment to lay out past ~5,000 words.
On a laptop, moving the mouse brings the control bar back; on the tablet, tap anywhere that is not a word.
If it isn't working
Open Setup and read the diagnostic lines at the bottom. They state whether speech recognition exists, whether the page is on a secure address, and how many words are loaded. That usually names the problem outright.
