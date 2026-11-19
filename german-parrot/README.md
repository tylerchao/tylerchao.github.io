# German Parrot 德文聽寫

German dictation practice in the browser: listen to a sentence (browser text-to-speech), type what you hear, get word-by-word feedback.

- Live: https://tylerchao.github.io/german-parrot/
- Single file: `index.html` (HTML + CSS + vanilla JavaScript, no build step)
- YouTube mode: paste a video URL + upload .srt/.vtt subtitles; each sentence plays its own clip and auto-pauses
- Accounts: email/password or Google sign-in (Firebase Auth); progress and custom lessons sync via Firestore (rules in `firestore.rules`)
- Built-in lessons in `lessons.js`: A1–C2, 5 topics per level, 10 sentences each
- Free video lessons (admins publish to `publicLessons`); own text/YouTube lessons are a Pro feature (`entitlements/{uid}.pro`)
- Features, custom lessons from pasted text, umlaut alternatives (ae/oe/ue/ss), capitalization check, speed control, light/dark mode, progress saved in localStorage
