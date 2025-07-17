# Ketta OS: A Natural Language Programmable GUI System

Ketta is a prototype AI operating interface inspired by the OS in the movie *Her*. It transforms natural language instructions into working GUI applications that interface directly with a Linux system via shell scripts.

> ⚠️ This is an early-stage base project. Active development is paused for now.

---

## 🧠 Concept

Ketta allows users to describe what they want using natural language. The system uses an AI model (Gemini) to convert this into a simple custom scripting language (`psudo.code`), which is then compiled into a Python PySide6 GUI.

These GUIs can execute shell scripts, list system information, perform actions, or act as launchpads—all without coding.

---

## 🧩 Components

### `AI.py`
- Core entry point for the Ketta AI assistant.
- Takes user input.
- Appends real-time `[SYSTEM CONTEXT]` (OS, GPU, RAM, etc.).
- Sends to Gemini (generative AI).
- Receives GUI code and saves it to `psudo.code`.
- Triggers the compiler.

### `compiler.py`
- Reads `psudo.code`.
- Validates and parses GUI + shell script definitions.
- Generates:
  - Executable shell scripts in `generated_scripts/`
  - GUI code in `code.py` (PySide6)
- Launches the GUI.

### `terminalapp.py`
- A standalone GUI terminal emulator.
- Uses `pyte` for proper terminal emulation.
- Integrates a full interactive bash shell.
- Supports UDP input on port `9000` (e.g., for external AI agents or control apps).

---

## 📦 Features (Implemented)

- ✅ Natural Language → GUI conversion
- ✅ Custom scripting DSL (`psudo.code`)
- ✅ Auto shell script generation and linking
- ✅ Real GUI (PySide6) with buttons, dropdowns, and inputs
- ✅ Script argument passing (e.g., from user inputs)
- ✅ Dynamic dropdown population via shell output
- ✅ Real terminal emulator with full bash access and UDP control

---

## 🚧 TODO (Future)

- [ ] Conversation memory for context-aware GUI generation
- [ ] Real-time voice input and feedback
- [ ] More interactive widgets (file dialogs, toggles, etc.)
- [ ] Backend plugin system for custom integrations
- [ ] Lightweight daemon mode

---

## 🔧 Usage

### Requirements
- Python 3.9+
- PySide6
- pyte
- Google Gemini access & API key

### Running the AI Assistant
```bash
python AI.py
```
### Running the Terminal App (Required to run single-line commands if necessary.)
```bash
python terminalapp.py
```
