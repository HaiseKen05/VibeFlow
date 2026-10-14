# MCU & Workflow Generator

A single-page web application (SPA) designed to document, style, and manage Microcontroller Unit (MCU) configurations, component pinouts, and procedural workflows. It features a live-updating text preview and direct local file system integration for saving configurations.

## ✨ Features

- **MCU & Component Management:** Define your primary microcontroller and attach multiple components, assigning specific pins (VCC, GND, and custom GPIO).
- **Drag-and-Drop Workflow Builder:** Create and reorder sequential logic steps for your hardware project using an intuitive drag-and-drop interface.
- **Local File System Library:** Utilizes the modern File System Access API to connect a local folder. Save and load MCU and Component configurations directly as `.json` files without downloading/uploading.
- **Live Stylized Output:** A real-time preview of your configuration formatted as a standardized text string. Customize the display with adjustable fonts, text sizes, background/text colors, and rich text formatting (bold, italic, underline).
- **One-Click Export:** Instantly copy the generated configuration string to your clipboard for use in documentation, code comments, or LLM prompts.

## 🛠️ Technology Stack

- **Markup & Styling:** HTML5, Tailwind CSS (via CDN)
- **Icons & Typography:** FontAwesome 6, Google Fonts (Inter, Fira Code)
- **Logic:** Vanilla JavaScript (ES6+)
- **Storage & APIs:** File System Access API (for local directory integration), IndexedDB (for persisting directory handles), Web Drag and Drop API.

## 🚀 Usage Guide

1. **Set the MCU:** Enter your target microcontroller (e.g., `Arduino Uno`, `ESP32`) in the top input.
2. **Add Components:** Click **Add Component** to define peripherals. 
   - Name the component.
   - Add standard or custom pins. Protected pins (like VCC/GND) are locked by default.
3. **Build the Workflow:** Add individual steps outlining the execution logic. Use the grip handle `⋮⋮` on the left of any step to drag and reorder the sequence.
4. **Add Notes:** Use the Notes section for extra context, I2C addresses, or specific library requirements.
5. **Customize Preview:** Use the toolbar above the dark preview pane to adjust the aesthetics of your output text.
6. **Save to Library:** 
   - Click the **Choose Library Folder** button to grant local folder access.
   - Save your specific MCU or Component setups for future projects. They will be stored as JSON files in `MCU/` and `Components/` subdirectories.
7. **Export:** Click **Copy Format** to copy the plain-text layout to your clipboard.

## 📁 Local Library Structure

When a local directory is linked, the app automatically manages the following structure:
```text
[Your Chosen Folder]/
├── MCU/
│   ├── Arduino_Uno.json
│   └── ESP32_WROOM.json
└── Components/
    ├── I2C_OLED_Display.json
    └── Servo_Motor.json
