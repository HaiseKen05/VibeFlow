# MCU & Workflow Generator

A single-page web application that helps you quickly draft and format microcontroller (MCU) configuration prompts — including components, pin assignments, workflow steps, and notes — into a clean, copy-ready text format. It also includes a local **Pin Library** that saves your MCU and component presets as JSON files inside folders you choose on your computer.

---

## Features

- **MCU Input** — Enter the name of your microcontroller (e.g., `Arduino Uno`).
- **Components & Pins** — Add multiple components, each with its own list of pins. `VCC` and `GND` are included by default and protected from deletion.
- **WorkFlow Builder** — Add ordered steps describing what the code should do.
- **Notes Section** — Attach extra instructions or pin configuration notes.
- **Live Output Preview** — See the formatted prompt update in real time as you type.
- **Copy Format** — One-click copy of the generated text to your clipboard.
- **Reset** — Restore the form to its default state.
- **Output Styling Controls** — Change the preview's font family, font size, text color, background color, and toggle bold / italic / underline.
- **Pin Library (Save & Load)** — Save MCU definitions and component presets into `MCU/` and `Components/` subfolders inside a directory of your choice, then reload them later.
- **File System Access API Support** — Saves directly into folders (Chrome, Edge, Opera). Falls back to downloading JSON files if the API is unavailable.
- **Persistent Folder Handle** — Remembers your chosen library folder between sessions using IndexedDB.

---

## Getting Started

1. **Save the file** as `index.html`.
2. **Open it** in a modern browser (Chrome, Edge, or Opera recommended for folder saving).
3. Fill in the form:
   - Enter your MCU name.
   - Add components and their pins.
   - Add workflow steps.
   - (Optional) Add notes.
4. Click **Copy Format** to copy the generated prompt, or use the **Copy** button in the preview panel.

No build step, no dependencies to install — everything is loaded from CDNs (Tailwind CSS, Font Awesome, Google Fonts).

---

## Using the Pin Library

### Choosing a Library Folder

Click **📂 Choose Library Folder** and select any folder on your machine. The app will create (or use) two subfolders inside it:

```text
YourChosenFolder/
├── MCU/
│   └── Arduino_Uno.json
└── Components/
    └── MyComponents.json
```

### Saving

- **Save MCU** — Saves the current MCU name and its pin list into `MCU/`.
- **Save Components** — Saves the entire component list into `Components/`.

### Loading

- Switch between the **MCU Folder** and **Components Folder** tabs.
- Click any saved item to load it into the form.
- Click the trash icon next to an item to delete it.

### Refresh & Re-grant

- Use **Refresh** to re-scan the chosen folder.
- If browser permission expires, click the folder button again to re-authorize.

### Fallback Behavior

If your browser doesn't support the File System Access API, the app will download the JSON file to your **Downloads** folder instead. You can still keep and manage these files manually.

---

## Output Format

The generated text follows this structure:

```text
Write an Arduino code with the following workflow

"MCU"
[Arduino Uno]

"Components"
- LED
  [VCC]
  [GND]
  [GPIO 7]

"WorkFlow"
[Arduino Uno initializes Serial Monitor]
↓
[Blinks LED on GPIO 7]
↓
[Wait 1 second]
↓
[Turn Off LED]
↓
[Wait 1 second]

"Notes"
[None]
```

Empty fields automatically fall back to their placeholder text.

---

## Tech Stack

| Technology | Purpose |
| --- | --- |
| HTML5 / CSS3 | Structure and styling |
| [Tailwind CSS](https://tailwindcss.com/) (CDN) | Utility-first styling |
| [Font Awesome](https://fontawesome.com/) (CDN) | Icons |
| [Google Fonts](https://fonts.google.com/) | Inter & Fira Code typefaces |
| Vanilla JavaScript | All app logic |
| File System Access API | Saving/loading JSON files into folders |
| IndexedDB | Persisting the chosen folder handle |

---

## Browser Compatibility

| Browser | Folder Saving | Fallback Download |
| --- | --- | --- |
| Chrome / Edge / Opera | ✅ | ✅ |
| Firefox | ❌ | ✅ |
| Safari | ❌ | ✅ |

For the best experience, use a Chromium-based browser.

---

## Keyboard & UI Tips

- The preview panel is **sticky** on desktop, so it stays visible while you edit.
- Click a saved library item to instantly load it into the form; the affected component card briefly highlights.
- Use the trash icons to remove components, pins, or workflow steps.
- The character count at the bottom of the preview updates live.

---

## License

This project is provided as-is for personal and educational use. Feel free to modify and adapt it to your needs.
