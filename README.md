# MCU & Workflow Generator

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.x-38B2AC?logo=tailwind-css)](https://tailwindcss.com/)
[![Font Awesome](https://img.shields.io/badge/Font_Awesome-6.4.0-339AF0?logo=fontawesome)](https://fontawesome.com/)

A lightweight, single-page web utility designed to build structured, formatted prompt configurations for microcontroller projects (e.g., Arduino, ESP32, STM32). It converts target MCU inputs and dynamic step-by-step logic workflows into a clean, standardized string format suitable for AI coding assistants, documentation, or code generation workflows.

---

## Features

- **Microcontroller Target Selection**: Specify any MCU platform (defaults to `Arduino Uno`).
- **Dynamic Workflow Builder**: Add, edit, or remove step-by-step logic nodes with real-time positional re-indexing.
- **Live Visual Preview**: Instant rendering of the formatted configuration string as you type, complete with live character and step counts.
- **One-Click Clipboard Export**: Modern Async Clipboard API integration with an explicit fallback mechanism for non-secure contexts (`execCommand`).
- **State Reset**: Quickly clear inputs and restore default template presets.
- **Zero Build Dependencies**: Runs entirely in the browser using CDN-delivered utilities (Tailwind CSS, Font Awesome, Google Fonts).

---

## Output Format Specification

The tool converts form inputs into a unified text block designed for structured LLM prompting or standard workflow specification:

```text
Write an Arduino code for the following format

"MCU"
[<MCU Name>]

"WorkFlow"
[Step 1]
↓
[Step 2]
↓
[Step 3]
```

---

## Tech Stack

- **HTML5 & Vanilla JavaScript**: Framework-free core application state and DOM manipulation.
- **Tailwind CSS (v3)**: Modern utility-first styling with dark mode aesthetic (`bg-slate-900`, `bg-slate-950`).
- **Font Awesome (v6.4.0)**: UI and status icon iconography.
- **Google Fonts**:
  - [Inter](https://fonts.google.com/specimen/Inter) for main UI elements.
  - [Fira Code](https://fonts.google.com/specimen/Fira+Code) for code/preview monospace rendering.

---

## Getting Started

Since this application is built as a single-page client-side web application, no server installation, node modules, or build steps are required.

### Local Execution

1. Clone or download this repository:
   ```bash
   git clone https://github.com/your-username/mcu-workflow-generator.git
   ```
2. Navigate to the project directory:
   ```bash
   cd mcu-workflow-generator
   ```
3. Open `index.html` directly in any web browser:
   ```bash
   # On macOS
   open index.html

   # On Linux
   xdg-open index.html

   # On Windows
   start index.html
   ```

---

## Project Structure

```
.
├── index.html        # Main HTML layout, styles, and inline application script
└── README.md         # Project documentation
```

### Application Functions Breakdown

| Function Name | Description |
| :--- | :--- |
| `initDefaults()` | Initializes UI state with default values and populates initial placeholder presets. |
| `renderWorkflowInputs()` | Dynamically updates the DOM list items for workflow steps based on state array changes. |
| `addWorkflowStep()` | Appends a new step object to state array and focuses the newly created input field. |
| `removeWorkflowStep(index)` | Deletes a workflow step by index and triggers a re-render and preview update. |
| `generateFormattedText()` | Compiles MCU input and workflow items into the final output format string. |
| `updateOutput()` | Updates live code preview area and dynamic character counts in real-time. |
| `copyToClipboard()` | Handles modern and fallback clipboard copy operations and triggers the toast notification. |
| `resetForm()` | Clears current inputs and re-initializes application state to defaults. |

---

## Customization

### Default Preset Workflow

To modify the default steps that populate on load or reset, update the `INITIAL_PRESET_STEPS` constant inside `index.html`:

```javascript
const DEFAULT_MCU_PLACEHOLDER = "Arduino Uno";
const INITIAL_PRESET_STEPS = [
    { value: "", placeholder: "Arduino Uno initializes Serial Monitor" },
    { value: "", placeholder: "Blinks LED on GPIO 7" },
    { value: "", placeholder: "Wait 1 second" },
    { value: "", placeholder: "Turn Off LED" },
    { value: "", placeholder: "Wait 1 second" }
];
```

---

## License

Distributed under the MIT License. See `LICENSE` for more information.
