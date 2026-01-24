# Simple Text To Speech (STTS) v1.5

**A clinical-grade, privacy-focused, offline-first Text-to-Speech tool for the browser.**

## About STTS

**Simple Text To Speech (STTS)** is a lightweight, single-file web application designed for professionals who need high-fidelity speech synthesis without compromising data privacy. Unlike cloud-based TTS services, STTS runs **entirely in your browser**. Your text never leaves your machine, making it ideal for reading aloud medical, scientific, or official documents during meetings, or helping students and trainees to listen to
sections of e-books and notes.

Developed by **Prof. Jyotirmay Kirtania**, STTS focuses on "reading fidelity"—ensuring that complex symbols, clinical units (like  or ), and technical formatting are handled intelligently rather than being skipped or garbled.

### Key Features

* **100% Offline & Private:** Uses the Web Speech API; no server-side processing.
* **LLM Clean-Up:** Automatically strips "AI noise" (emojis, markdown artifacts, and fenced code) when pasting from LLMs like ChatGPT or Claude.
* **Clinical Symbol Dictionary:** A built-in, editable dictionary that translates symbols (e.g., `≥` to "greater than or equal to") into spoken words.
* **Smart Section Detection:** Automatically breaks long documents into sections based on headers or paragraph blocks for easy navigation.
* **High Capacity:** Supports up to 1,000,000 characters.
* **No Installation:** A single HTML file that runs in any modern browser (Chrome, Edge, Safari, Firefox).

---

## Help & User Guide

### Getting Started

1. **Open the Tool:** Simply open the `STTS-v1.4.html` file in your preferred web browser.
2. **Input Text:** * **Paste:** Copy and paste text directly into the main text area.
* **Upload:** Use the "Choose File" button to load `.txt`, `.md`, `.html`, or `.pdf` (text-based) files.


3. **Select a Voice:** Choose from your system's native voices in the "Native Browser Voices" dropdown.

### Controlling Playback

* **Play All:** Reads the entire document from start to finish.
* **Play Section:** Reads only the currently selected section (detected from headings).
* **Play Selection:** Highlight a specific sentence or paragraph with your mouse and click this to read only that portion.
* **Rewind/FF:** Jumps forward or backward by approximately 3 "chunks" of text.
* **Loop:** Use the Loop dropdown to repeat the selection, section, or the entire document a specific number of times.

### Read Modes (Fidelity)

In the **Read Mode** dropdown, you can choose how the engine treats your text:

* **Plain:** Maximum fidelity. No stripping. Best for medical lists and technical data.
* **Clean:** Removes HTML/Markdown tags but keeps most punctuation. (Recommended for most users).
* **Aggressive:** Strips almost all non-alphanumeric characters for a "smooth" listen.

### The Symbol Dictionary

The **Symbol Dictionary** panel allows you to control how the TTS engine pronounces specific characters.

* **Format:** `symbol = spoken word` (e.g., `↑ = increase`).
* **Customization:** You can add your own shorthand or clinical jargon. Click **Apply to text** to permanently swap these symbols in your input box, or let the engine handle them "on the fly" during playback.

### Tips for Best Performance

* **For PDF Users:** This tool extracts text from "clean" PDFs. If your PDF is a scanned image, you must perform OCR on it before importing.
* **Natural Voices:** On Windows and macOS, look for voices labeled "Natural," "Neural," or "Online"—these usually offer the highest quality prosody.
* **Clearing Data:** Use the **Clear** button to reset the text area and stop all active speech instantly.

---

## License

Licensed under the **GNU GPL v3**.

Copyright (C) 2026 Prof. Jyotirmay Kirtania.
