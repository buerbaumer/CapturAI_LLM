<img width="1220" alt="image" src="https://github.com/user-attachments/assets/093635b2-2e3b-4832-97a2-5a747a3bebef" />


# Screen Capture + Sub-Selection Analysis + Chat
# 100% generated via chatgpt o1 pro mode

This repository contains a single-page web application that allows you to:
- Capture your screen and take either full or sub-region screenshots.
- Annotate the captured screen with freehand drawings (Edit Mode) and text (Text Mode).
- Interact with an integrated chat panel that can send your current screenshot (or its selected area) to an OpenAI API endpoint for further analysis.

It leverages the browser's `navigator.mediaDevices.getDisplayMedia` API for screen capture, along with HTML `<canvas>` elements and JavaScript for annotations, zooming, undo/redo, and more.

## Table of Contents
- [Features](#features)
- [Installation and Setup](#installation-and-setup)
- [Usage Guide](#usage-guide)
  - [1. Start Screen Capture](#1-start-screen-capture)
  - [2. Enter OpenAI API Key](#2-enter-openai-api-key)
  - [3. Taking Screenshots](#3-taking-screenshots)
  - [4. Annotation Modes](#4-annotation-modes)
  - [5. Undo/Redo](#5-undoredo)
  - [6. Zoom In/Out](#6-zoom-inout)
  - [7. Clear Selection](#7-clear-selection)
  - [8. Chat Panel](#8-chat-panel)
- [File Overview](#file-overview)
- [Browser Support](#browser-support)
- [Contributing](#contributing)
- [License](#license)

---

## Features

1. **Screen Capture**  
   Uses the native [Screen Capture API](https://developer.mozilla.org/en-US/docs/Web/API/Screen_Capture_API) to record your screen (or any specific window/application).  
   
2. **Full Screenshot or Rectangular Selection**  
   - **Full Screenshot**: Capture the entire screen or application window.  
   - **Sub-Selection**: Click-and-drag to select a rectangular region of the live screen feed; then store that sub-region as an image for analysis or chat.

3. **Annotation**  
   - **Edit Mode (Freehand Drawing)**: Draw lines of adjustable color and thickness.  
   - **Text Mode**: Insert text labels with editable font size and color.  
   - **Undo/Redo**: Maintains a stack of actions (drawing lines, adding text) to revert or reapply changes.

4. **Zoom**  
   - Incrementally zoom in or out of the captured screen to inspect finer details or see more area at once.

5. **Chat Integration**  
   - An on-page chat UI that allows you to send your image (full or the selected region) along with text prompts to an OpenAI API.  
   - Each response from the assistant is displayed in the chat panel, with support for code blocks, formatting, and a copy-to-clipboard feature.

6. **Lightweight & Self-Contained**  
   Everything is included in a single HTML file (with inline CSS and JavaScript). Simply open it in a modern browser to get started.

---

## Installation and Setup

1. **Clone or Download** this repository to your local machine.

2. **Open the file** `index.html` (or whatever you have named the HTML file containing this code) in a modern browser such as Google Chrome, Microsoft Edge, or Firefox (some browsers may have partial support for `getDisplayMedia`, so Chrome or Edge is recommended).

3. **Allow Screen Capture** when prompted. The browser will ask you which screen or application window you want to share.

> **Note**: If you open this file directly from the filesystem (using `file://`), some browsers or OS settings may prevent full functionality. If you run into issues, consider using a local HTTP server (for example, `python -m http.server`) and then open `http://localhost:8000/index.html`.

---

## Usage Guide

Once the page loads, you'll see two sections:  
- The **left** side for screen capture and annotations.  
- The **right** side for the chat interface (hidden initially, until you start screen capture).

### 1. Start Screen Capture
- Click **Start Screen Capture**.  
- Your browser will prompt you to choose which screen or window to share.  

Once you allow access, the captured stream will appear on the left canvas.

### 2. Enter OpenAI API Key
- Click the **Enter API Key** button.  
- Provide your `sk-...` key from OpenAI.  
  - This will be used by the chat panel to send your text prompt and screenshot (or selected region).  
  - If you do not provide a valid key, the chat panel will remind you to enter one before continuing.

### 3. Taking Screenshots
- **Full Screenshot**: Click **Full Screenshot** to save the entire captured screen as `full_screenshot.png`.  
- **Rectangular Selection**:  
  - By default (when not in Edit Mode or Text Mode), click and drag over the canvas to draw a selection rectangle.  
  - This sub-region is stored internally and can be sent to the chat or replaced if a new selection is made.

### 4. Annotation Modes
- **Edit Mode (Drawing)**  
  - Toggle this mode with **Start Edit Mode** / **Exit Edit Mode**.  
  - When active, you can draw freehand lines.  
  - Adjust **Line Thickness** and **Line Color** in the controls that appear.  
- **Text Mode**  
  - Toggle this mode with **Start Text Mode** / **Exit Text Mode**.  
  - Click anywhere on the captured image to create a text field.  
  - Adjust **Font Size** and **Font Color** in the controls that appear.  
  - Press **Enter** to finalize the text or **Esc** to cancel.  
  - Press **Delete** (when editing existing text) to remove it.  
  - You can drag the text field before confirming by clicking the small "Drag here" handle.

### 5. Undo/Redo
- **Undo** reverses your last action (adding a line, adding text, removing text, etc.).  
- **Redo** reapplies an action that was undone.  

> The Undo/Redo system only tracks annotation actions; it does not revert screenshot selection.

### 6. Zoom In/Out
- **Zoom In**: Increases the scale factor, making the canvas larger.  
- **Zoom Out**: Decreases the scale factor, making the canvas smaller.  
> Repeatedly click these buttons to incrementally zoom.

### 7. Clear Selection
- Removes the last rectangular selection and all annotations (drawn lines, text).  
- Essentially resets the canvas state.

### 8. Chat Panel
- Once screen capture starts, the chat panel on the right becomes visible.  
- Type your message in the text box, then click **Send**.  
  - The chat will attempt to send your text and the selected region (or entire screen if no selection was made) to OpenAI via the provided API key.  
- The assistant's response is displayed below your message.  
  - Code blocks in the assistant's message are rendered in a `<pre><code>` block.  
  - Each assistant message has a small **Copy** button in the bottom-right corner to copy its entire contents to clipboard.

---

## File Overview

Only one primary file is included (though it may be named `index.html` or something similar):

- **`index.html`**  
  Contains all HTML, CSS, and JavaScript inlined. When opened in a modern browser:
  - Prompts for screen capture.  
  - Manages annotation and text.  
  - Integrates a basic chat UI on the right side.  
  - Sends requests to the OpenAI API when you chat.

---

## Browser Support

- **Google Chrome / Edge** (Recommended): Full support for `navigator.mediaDevices.getDisplayMedia`.  
- **Firefox**: Mostly supported, but some known quirks may occur with screen capturing.  
- **Safari**: Limited or partial support depending on version.  

Always ensure you grant the necessary permissions for screen capture.

---

## Contributing

1. Fork this repository.  
2. Create a feature branch for your changes (`git checkout -b feature/new-feature`).  
3. Commit your changes (`git commit -m 'Add some feature'`).  
4. Push to the branch (`git push origin feature/new-feature`).  
5. Open a Pull Request describing your changes.  

Bug reports and feature requests can be submitted via [GitHub Issues](../../issues).

---

## License

Licensed under the [MIT License](./LICENSE). Feel free to use this code as a starting point for your own projects, or contribute improvements back here!

