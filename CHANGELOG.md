# Changelog

All versions of VoiceFlow AI. Installers: [Releases](https://github.com/imomzoda-dev/VoiceFlowAI/releases).

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

