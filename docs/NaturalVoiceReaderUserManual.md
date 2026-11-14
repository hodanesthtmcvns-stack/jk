# Natural Voice Reader — User Manual

Version 3.0 · November 2026
© Prof J Kirtania · Free software under the GNU General Public License 3.0

---

## 1. What it is

Natural Voice Reader reads textbooks, papers and documents aloud using the speech voices already installed on your device. It is a single HTML file. It needs no installation, no account, no subscription and no internet connection.

It is built for medical students and residents who want to listen to a chapter before studying it in depth: to become familiar with the content, the terminology and the flow of ideas.

**What it does**

- Opens PDF, EPUB and plain-text files, including large textbooks (tested up to about 500 MB).
- Reads the body text as continuous prose and leaves out what does not make sense when heard: tables, figures, page numbers, footnotes, front matter, appendices, reference lists, citation markers, web addresses and cross-references.
- Speaks numbers, units and clinical shorthand as words ("4–6 mg/kg IV" is read as "4 to 6 milligrams per kilogram I V").
- Shows the book's chapters and sections so you can choose exactly what to hear.
- Remembers your place in each book and lets you set your own bookmarks.

**What it is not**

It is a listening aid for learning. It is not a clinical reference. Do not take a drug dose, threshold or formula from what you hear without checking it against the printed page (see section 12).

---

## 2. Requirements

| Item | Requirement |
|---|---|
| Browser | A current version of Chrome, Edge, Firefox or Safari |
| EPUB files | Chrome or Edge 103+, Firefox 113+, Safari 16.4+ |
| Voices | At least one English speech voice installed on the device |
| Internet | Not needed |
| Memory | For very large PDFs, roughly the size of the file in free RAM |

**Installing a better voice.** Voice quality depends entirely on your device. If the voice sounds robotic, install a higher-quality English voice:

- **Windows:** Settings → Time & language → Speech → Manage voices → Add voices.
- **macOS / iOS:** Settings → Accessibility → Spoken Content → Voices → English → download an "Enhanced" or "Premium" voice.
- **Android:** Settings → Accessibility → Text-to-speech output → install voice data for your speech engine.

Restart the browser after installing a voice.

---

## 3. Quick start

1. Double-click `NaturalVoiceReader.html` to open it in your browser.
2. Click **＋ Open file** and choose a PDF or EPUB, or drag the file onto the text box.
3. Wait for the status line to show **Loaded**. A typical 1,000-page textbook takes 5 to 20 seconds.
4. In the section list under the text, click the chapter you want. Reading starts there.
5. Use **Pause**, **Stop**, **◂ Back** and **Skip ▸** as needed. Your place is remembered.

---

## 4. The screen

**Left side — your text**

- **Text box.** Shows the text that will be read. You can paste or type into it.
- **Now-reading panel.** Shows the passage being spoken, its number and its section.
- **Bookmarks panel.** Your saved places in this document.
- **Section list.** Appears when a PDF or EPUB is open.

**Right side — voice and playback**

- Voice, reading profile, speaking rate and pitch.
- Playback buttons and the progress bar.
- The "Leave out" filters.
- The character-repair field.
- The pronunciation guide.

**☾ Theme** (top right) switches between light and dark.

---

## 5. Opening text

| Method | How |
|---|---|
| Open a file | **＋ Open file** → choose a file |
| Drag and drop | Drop a file onto the text box |
| Paste | **Paste**, or use the keyboard in the text box |
| Type | Type directly in the text box |
| Clear | **Clear** empties the box. It also cancels a file that is still loading |

**Supported files:** `.pdf`, `.epub`, `.txt`, `.md`, `.html`, `.htm`, `.csv`, `.log`.

**PDF notes**

- The PDF must contain a text layer. A digitally produced PDF has one. A scanned book needs OCR first; the app tells you if no text layer is found.
- Password-protected PDFs cannot be opened. Remove the password first.

**EPUB notes**

- DRM-protected EPUBs cannot be read.
- Files over 4 GB, or with more than 65,535 internal files, are not supported.

**Large documents.** When a book has more than about 1.5 million characters, the text box shows only the section being read and becomes read-only. Playback, the section list, bookmarks and resume still work over the whole book.

---

## 6. Playback

| Control | Action |
|---|---|
| **▶ Play** | Starts reading. Continues from your saved place if there is one |
| **Ⅱ Pause / ▶ Resume** | Pauses; resumes from the start of the same passage |
| **■ Stop** | Stops. Your place is kept; **Play** continues from it |
| **⏮ Start** | Returns to the beginning of the text |
| **◂ Back** | Moves back one passage |
| **Skip ▸** | Moves forward one passage |
| Progress bar | Click anywhere on it to jump to that point |
| `Ctrl` + `Enter` (`⌘` + `Enter` on Mac) | Play |
| `Esc` | Stop |

A *passage* is one or two sentences. Headings and bullet points are separate passages, and a heading is followed by a short silence so that you can hear the structure.

**Voice settings**

| Setting | Range | Default |
|---|---|---|
| English voice | Voices installed on your device | First available |
| Reading profile | See section 10 | Medical |
| Speaking rate | 0.65× to 1.5× | 0.85× |
| Pitch | 0.7 to 1.3 | 1.05 |

Rate and pitch changes take effect from the next passage.

---

## 7. Choosing what to hear: the section list

When a PDF or EPUB is open, the list under the text shows every chapter, section and subsection, indented by level.

| Element | Meaning |
|---|---|
| ☑ tick box | This section will be read. Ticking a section ticks everything nested under it |
| ▣ partly filled box | Some, but not all, of the subsections are ticked |
| 🔖 | The entry comes from the book's own bookmarks (PDF) or table of contents (EPUB) |
| Title (click) | Read from here onwards |
| **only** | Untick everything else and read just this part |
| `FRONT` / `BACK` tag | Detected as front matter or back matter; unticked automatically |
| Word count | Words in this section and everything under it |

**Buttons above the list**

| Button | Action |
|---|---|
| List filter | Show **All headings**, **Bookmarks only**, **Level 1** or **Levels 1–2**. This changes only what is listed, not what is read |
| **Auto** | Restore the automatic selection |
| **All** | Tick every section |
| **None** | Untick every section, so you can tick only the ones you want |

**Common tasks**

- *Listen to one chapter:* click **only** on that chapter.
- *Listen to three topics from different chapters:* click **None**, tick the three topics, press **Play**.
- *Hear the preface or an appendix:* tick it. The automatic choice is only a default.

The line under the document name summarises what was found, what was left out, and what was restored. Example: number of pages, number of document bookmarks, sections ticked, items left out by type.

---

## 8. Resume and bookmarks

**Resume.** Your place is saved whenever you pause, stop or skip, and every few passages while reading. It is stored per document. When you open the same file again, **Play** continues from where you stopped.

**Bookmarks**

1. Move to the passage you want (pause there, or use Back/Skip).
2. Click **＋ Bookmark**.
3. The bookmark appears in the Bookmarks panel, named after its section and first words.

| Bookmark control | Action |
|---|---|
| ▶ | Read from this bookmark |
| Name field | Click and type to rename |
| ✕ | Delete the bookmark |

Places and bookmarks are kept in this browser on this device only, for the 60 most recently used documents. They are not removed by unticking the "Remember" box. Clearing your browser's site data removes them.

If a bookmark lies in a section you have unticked, the app tells you; tick that section and try again.

---

## 9. What is left out

These filters apply when a PDF or EPUB is opened. Each can be switched off. A change is applied to the open document immediately.

| Filter | What it removes |
|---|---|
| Tables, figures and their captions | Table rows, figure labels, captions, credit lines such as "Reproduced from…" |
| Page numbers, running headers and footers | Text repeated at the top or bottom of pages |
| Footnotes and endnotes | Small-print notes at the foot of a page or column |
| Front matter | Title page, copyright, contents, preface, contributors, abbreviations |
| Appendices, references, index | Appendices, reference lists, "Further reading", index pages, bibliography entries |
| Reference markers | `[12]`, `(12)`, superscript numbers, † ‡ *, DOI strings, web addresses, email addresses |
| Cross-references | "(see p. 12)", "(Fig. 3.1)", "(Table 4.2)", "See also" lists |
| Reference numbers fused to words | In PDF text only: `outcomes12`, `shown.3` |

Citations written as "(12)" are removed only when the book uses that style throughout. A numbered list such as "(1) … (2) … (3) …" is kept.

---

## 10. Reading profiles

The profile decides how written text is turned into spoken words. The text on screen is never changed.

| Profile | Use for |
|---|---|
| **Medical** (default) | Clinical textbooks and papers |
| General English | Ordinary prose |
| Scientific | Science text with units |
| Technical | Software and engineering text |
| Financial | Finance and accounting text |
| Legal | Statutes and legal documents |
| Administrative | Office files, orders and procurement papers |

**All profiles** turn symbols and punctuation into words or pauses:

| Written | Spoken |
|---|---|
| ≥ ≤ > < ± | "greater than or equal to", "less than or equal to", "greater than", "less than", "plus or minus" |
| ↑ ↓ | "increased", "decreased" |
| α β γ μ | "alpha", "beta", "gamma", "mu" |
| e.g. / i.e. / etc. / vs. | "for example", "that is", "et cetera", "versus" |
| 38.5°C | "38.5 degrees Celsius" |
| Dashes, slashes, bullets | Short pauses |
| ▯ | "blank" (see section 11) |

**The Medical profile** also handles:

| Written | Spoken |
|---|---|
| 4–6 | "4 to 6" |
| 1:200 000 | "1 in 200000" |
| 30:2 | "30 to 2" |
| 0.5 mL/kg/h | "0.5 millilitres per kilogram per hour" |
| 65 mmHg, 5 cmH2O, 8 kPa | "millimetres of mercury", "centimetres of water", "kilopascals" |
| mcg, µg, mmol/L, mEq/L, g/dL | Spelled out in full |
| SpO2, PaO2, FiO2, EtCO2 | Spoken letter by letter; EtCO2 as "end tidal C O 2" |
| O2, N2O, K+, Na+, HCO3− | "oxygen", "nitrous oxide", "potassium", "sodium", "bicarbonate" |
| IV, IM, SC, PO | "I V", "I M", "subcutaneous", "P O" |
| od, bd, tds, qds, prn, q4h | "once daily", "twice daily", "three times daily", "four times daily", "as needed", "every 4 hours" |
| class III, factor VIII, ASA IV | "class 3", "factor 8", "ASA 4" |
| 18G | "18 gauge" |

The **Scientific** profile applies the number and unit rules without the clinical shorthand.

---

## 11. Characters, repair and pronunciation

### 11.1 Characters restored automatically

Many publishers' fonts do not tell the computer what some of their glyphs mean. A digit, an "fi" ligature, a bullet or an arrow can arrive as a blank or as a stray letter. The app examines how each such glyph is used across the whole book and restores it when the evidence is clear. Examples:

- A font that never produces the digit 1, together with an unknown glyph that always sits among digits: the glyph is read as 1.
- Unknown glyphs inside words: restored as fi, fl, ff, ffi or ffl.
- Letters from a symbol font used as arrows, bullets, Greek letters or comparison signs.

The line under the document name reports this as **restored from font evidence**, with counts.

### 11.2 Unreadable characters

A character that cannot be identified is **never guessed**. It is shown as **▯** in the text and spoken as "blank". The document line lists its code and how often it occurs, for example:

> ⚠ unreadable characters shown as ▯: U+E123 ×214

If you know what the character stands for (check the printed page), enter a rule in **Repair unreadable characters**:

| Rule | Meaning |
|---|---|
| `U+E123=1` | Replace the character with code U+E123 by `1` |
| `¦=1` | Replace the literal character `¦` by `1` |
| `U+E123=1, U+E124=fi` | Several rules, separated by commas |

The rule applies to the whole document at once.

### 11.3 Pronunciation guide

Use this to correct how a term is spoken. One rule per line:

```
TMC = T M C
NIH = N I H
R0 = R zero
```

Format: `text = spoken version`. Matching ignores upper and lower case and applies to whole words. These rules are applied before the reading profile.

---

## 12. Accuracy and safe use

Read this section before relying on the app for study.

1. **Listen in a safe setting.** Use it during low-attention tasks in a safe environment. Do not use it while driving or during clinical work.
2. **Numbers can be wrong.** Restored digits and signs are inferred from the book's fonts. The inference is strong for fonts with many numbers and weaker for small fonts used in boxes and algorithms. Verify every dose, rate, threshold and formula against the printed page before using it.
3. **A lost character may leave no trace.** If a file yields nothing at all for a glyph, no ▯ appears and the number is simply short. A dose that sounds too small or too large should be checked.
4. **Tables, figures, algorithms and equations are not read.** Important content often lives there. Return to the book for them.
5. **Structure detection is automatic.** A section may occasionally be classed as front or back matter by mistake. Check the section list and tick what you need.
6. **Abbreviations follow fixed choices.** For example, "SC" is always read as "subcutaneous". Use the pronunciation guide to override a choice.
7. **Respect copyright.** Open only books and papers you are entitled to use.

---

## 13. Privacy and storage

- Files are read inside the page. Nothing is sent to any server.
- **Remember text and settings on this device** stores your text, voice, rate, pitch, profile, filters and rules in this browser. Untick it to delete them. Text from very large books is not stored; reopen the file instead.
- Reading positions and bookmarks are always stored in this browser (section 8).
- To remove everything, clear the site data for the file in your browser settings.

---

## 14. Troubleshooting

| Problem | Likely cause and remedy |
|---|---|
| "No English voice found" | No English voice is installed, or the browser has not loaded voices yet. Install a voice (section 2) and reload the page |
| Nothing is heard | Check the device volume and that a voice is selected. On phones, tap **Play** again after the page has loaded |
| Speech stops when the phone screen locks | Browsers stop speech when the screen is off. Keep the screen on; the app asks the device to stay awake while reading |
| "This PDF has no usable text layer" | The PDF is a plain scan. Run OCR on it and open the OCR version |
| "Password-protected" | Remove the password in a PDF tool, then reopen |
| "DRM-protected" EPUB | The file is encrypted by the seller and cannot be read |
| A large file is slow or the tab closes | The device has too little free memory. Close other tabs and apps, or use a computer |
| A chapter is missing | It may be unticked. Find it in the section list and tick it, or click **All** |
| References or captions are still read | Detection is automatic and a few may get through. Untick that section, or skip with **Skip ▸** |
| ▯ appears in the text | See section 11.2 |
| A term is mispronounced | Add a rule in the pronunciation guide (section 11.3) |
| Rate and pitch are not the stated defaults | Settings saved from an earlier version are being used. Move the sliders to the values you want |
| Wrong reading order on a page | Complex layouts (three columns, boxed sidebars) can confuse column detection. Skip that passage |

---

## 15. Known limits

- English text only.
- PDFs need a text layer; the app does not perform OCR.
- Mathematical equations and chemical structures are not readable aloud.
- Footnotes are recognised by their smaller type. If a scan's OCR made all text the same size, footnotes will be read.
- A word broken across lines with a hyphen is joined, so a true hyphenated compound split at a line end loses its hyphen.
- Voice quality, and whether voices work offline, depend on the device.

---

## 16. Licence and credits

Natural Voice Reader
Copyright © November 2026 Prof J Kirtania

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License, version 3, as published by the Free Software Foundation. It is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See <https://www.gnu.org/licenses/gpl-3.0.html>.

PDF reading uses the embedded Mozilla pdf.js library (version 3.11.174), licensed under the Apache License 2.0.
