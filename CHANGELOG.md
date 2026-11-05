# Changelog

All versions of VoiceFlow AI. Installers: [Releases](https://github.com/imomzoda-dev/VoiceFlowAI/releases).

## 1.0.5 — 2026-11-05

**VoiceFlow AI 1.0.5** — dictation that keeps working. For **Windows** and **macOS**.

- **Fixed: after a few dictations, every one failed with “Something went wrong”.** Disk cleaners deleted VoiceFlow's working folder in the system temporary folder while the app ran. Working files now live in VoiceFlow's own folder, which is recreated before every phrase.
- **Safer model downloads:** the SHA-256 check now reads the finished file on disk, and a resumed download continues from the file's real size.

## 1.0.4 — 2026-11-05

**VoiceFlow AI 1.0.4** — reliable model downloads.

- **Downloads continue after a dropped connection.** If the connection drops or stalls while a model downloads, it continues from where it stopped instead of failing. The file is still checked with SHA-256 from start to finish before it is used.

## 1.0.3 — 2026-11-04

**VoiceFlow AI 1.0.3** — Tajik and Persian recognised properly, every language in its own alphabet.

- **Tajik model.** Whisper's general models know very little Tajik: they wrote Tajik speech in Latin letters (“Nomi man …”) or Persian script. VoiceFlow now offers a **Tajik language model** (190 MB, one click in *Settings → Recognition*), used automatically when you dictate in Tajik. On Google FLEURS Tajik recordings: **5% word errors and 100% Cyrillic** — the general Large v3 Turbo model made more errors than there were words (102%) and wrote only 28% in Cyrillic.
- **Persian model.** A new **Persian language model** (574 MB), trained on conversational speech too, with punctuation: **6% word errors** instead of 20–29% with the general model. Phrases no longer repeat themselves (beam search on the GPU, and as a fallback on the CPU).
- **Every language in its own alphabet.** VoiceFlow knows the alphabet of all ~100 languages. When recognition comes out in the wrong one (Tajik in Latin letters, Urdu in Hindi script…), the phrase is recognised again with a short sentence in the right alphabet as a guide. Latin look-alike letters inside Cyrillic words are fixed; Persian gets «ی», «ک» and «می‌».
- **Right-to-left text.** Persian, Arabic, Urdu and Hebrew read right-to-left in documents, history and the dictation widget, next to left-to-right text.
- **Fixed: long phrases were cut in the middle of a word.** When you speak for more than 9.5 s without a pause, the phrase is now cut in the gap between two words.
- **Tajik punctuation:** the Tajik model writes no punctuation, so VoiceFlow starts the dictation with a capital letter and ends it with a full stop. Turn on *AI Writing → Correct* to have commas added too.

**Updating:** VoiceFlow AI shows an **Update** button in the sidebar, or run `VoiceFlow-AI-Setup-1.0.3.exe` — it shows **“Update 1.0.2 → 1.0.3”** and keeps all your data. Then open *Settings → Recognition* and download the model for your language.

**Windows:** the installer is not code-signed — if SmartScreen warns, click *More info → Run anyway*.

## 1.0.2 — 2026-11-04

**VoiceFlow AI 1.0.2** — recognition that always hears you, and is many times faster.

- **Fixed: “Speech not detected” while you were speaking clearly.** With large models on the CPU, a long phrase could take 20–30 s to recognise. A 15-second safety timer then ran out and showed “Speech not detected” even though your speech had been recorded. The timer now only reacts if the microphone really delivered nothing.
- **~4× faster on the processor.** The engine now uses a 10-second window, and long speech is split into phrases of up to 9.5 s at the quietest moment, so words are never cut. Large v3 Turbo on an i9-9900K: an 8.7 s phrase now takes **≈ 6 s instead of 20–30 s**, with the same text.
- **NVIDIA GPU acceleration.** If you have an NVIDIA graphics card, *Settings → Recognition* offers **GPU acceleration** (one click, ≈ 685 MB). GTX 1050 Ti: the same phrase in **0.8 s** with Large v3 Turbo. If the GPU can't be used, VoiceFlow switches back to the CPU automatically. Settings also show which engine is running and how fast your last phrase was.
- **The microphone always comes first.** Recognition runs at lower priority, so it can never interrupt recording, even while the next phrase is recognised during live typing.
- **With live typing off,** the whole text is inserted once at the end.

**Updating:** VoiceFlow AI **1.0.0 / 1.0.1** shows an **Update** button in the sidebar, or run `VoiceFlow-AI-Setup-1.0.2.exe` — it shows **“Update 1.0.1 → 1.0.2”** and keeps all your data.

**Windows:** the installer is not code-signed — if SmartScreen warns, click *More info → Run anyway*.

## 1.0.1 — 2026-11-04

**VoiceFlow AI 1.0.1** — choose your language with one key, and text that appears while you speak. For **Windows** and **macOS**.

- **Pick the language when you start.** Press **F12** (⌥ on a Mac): the dictation widget shows your three languages. Choose with **← →** (or **1 2 3**, or a click) — after **2 seconds** dictation starts in that language, or press F12 again to start at once. The time to choose can be 2, 4, 6 or 8 seconds (*Settings → Voice*).
- **No more wrong languages.** In *Settings → Recognition → Your languages* choose your default language and two more — speech is recognised in these only. Russian can no longer come out as “Icelandic”. **All ~100 languages** Whisper knows can be chosen.
- **Types while you speak, like Google Docs.** Every phrase appears at the cursor as soon as you pause, while you keep talking. Can be turned off in *Settings → Voice*.
- **Nothing is lost.** The dictated text is also left on the clipboard: if no text field had focus, just press **Ctrl+V / ⌘V**. The widget says *Copied*.
- **Much faster local recognition.** whisper.cpp now keeps the model loaded (it starts while you choose the language), so phrases are recognised without reloading it each time.
- **Installer that updates.** Running the installer over an installed VoiceFlow AI shows **“Update 1.0.0 → 1.0.1”** with an **Update** button; your folder, documents, models, keys and settings are kept.

**Updating:** VoiceFlow AI **1.0.0** shows an **Update** button in the sidebar. The earlier test build **0.1.0** has no built-in updater — download `VoiceFlow-AI-Setup-1.0.1.exe` once; it updates in place.

**Windows:** the installer is not code-signed — if SmartScreen warns, click *More info → Run anyway*.

## 1.0.0 — 2026-11-04

**VoiceFlow AI 1.0.0** — the first release. Voice typing in any app and an AI document workspace, for **Windows** and **macOS**.

- **Hold a key, speak, release.** Text appears at the cursor in any app — Word, Google Docs, Telegram, WhatsApp, Chrome, Safari, VS Code, Notion. Hold, toggle or button mode; F12 on Windows, **Right Option (⌥)** on a Mac; any key or combination, with conflict detection.
- **Dynamic-Island dictation widget** at the top of the screen: live waveform, timer, detected language and every step. It never takes focus from the app you are typing in, and your clipboard is restored after pasting.
- **Private by default.** Speech is recognised on your computer with **whisper.cpp** — models are downloaded only when you click and checked with SHA-256. OpenAI, Groq, Anthropic, Ollama, LM Studio and faster-whisper servers can be added with your own keys (encrypted with Windows DPAPI / macOS Keychain); nothing goes to the cloud until you allow it.
- **Made for Tajik.** Automatic language detection, or *“among Tajik, Russian and English”*: when Whisper mistakes Tajik for Russian or Persian, the app sees ғ қ ӯ ҳ ҷ ӣ in the text and recognises it again in Tajik. Mixed speech stays mixed, nothing is translated unless you ask.
- **Raw, Correct and Professional** processing with Tajik and Russian grammar rules. The original, corrected and final text are kept in History with a word-by-word comparison; if the AI fails or changes too much, the original is inserted.
- **Documents:** headings, lists, tables, images, links · dictation into the document · voice commands (*“new paragraph”*, *“абзаци нав”*, *“translate to English”*…) · an AI assistant that shows every change before applying it · autosave, crash recovery, version history · DOCX, PDF, Markdown, TXT, HTML export with Tajik letters · 10 templates.
- **iOS-style interface** in light and dark, six accent colours, a ⌘K / Ctrl+K command palette, English, Russian and Tajik.
- **Updates inside the app:** when a new version is out, an **Update** button appears in the sidebar — download, SHA-512 check, *Restart and update*.

**Windows** 10/11 x64: `VoiceFlow-AI-Setup-1.0.0.exe`. **macOS** 12+: `VoiceFlow-AI-1.0.0-arm64.dmg` (Apple Silicon) or `VoiceFlow-AI-1.0.0-x64.dmg` (Intel).

**First steps:** *Settings → Recognition* → **Download whisper.cpp** (Windows) or `brew install whisper-cpp` (macOS), then download the **Large v3 Turbo (quantised)** model (≈ 550 MB).

> [!IMPORTANT]
> **macOS, new install from the DMG:** drag the app into *Applications*, then **before the first start** open **Terminal** and run:
> ```bash
> xattr -dr com.apple.quarantine "/Applications/VoiceFlow AI.app"
> ```
> Without it macOS refuses to open an app that is not signed by Apple. Once per installation; in-app updates need nothing. Then allow *Microphone*, *Accessibility* and *Input Monitoring* when asked.

**Windows:** the installer is not code-signed — if SmartScreen warns, click *More info → Run anyway*.

