# German Parrot 德文聽寫

German dictation practice in the browser: listen to a sentence (browser text-to-speech), type what you hear, get word-by-word feedback.

- Live: https://tylerchao.github.io/german-parrot/
- Single file: `index.html` (HTML + CSS + vanilla JavaScript, no build step)
- YouTube mode: paste a video URL + upload .srt/.vtt subtitles; each sentence plays its own clip and auto-pauses
- Accounts: email/password or Google sign-in (Firebase Auth); progress and custom lessons sync via Firestore (rules in `firestore.rules`)
- Features: 4 built-in lessons (A2–B1), custom lessons from pasted text, umlaut alternatives (ae/oe/ue/ss), capitalization check, speed control, light/dark mode, progress saved in localStorage
