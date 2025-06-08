# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.2.0] - 2025-06-08

This release introduces a major new personalization feature—a complete custom theme editor—and a key quality-of-life improvement to ensure hotkey settings are always up-to-date.

### ✨ Added
- A powerful **Custom Theme Editor** accessible via `View > Themes > Custom...`.
- Users can now customize all major interface colors, from backgrounds and text to accents and borders, using a simple color picker interface.
- Custom themes are automatically saved and reloaded when the application starts.
- A "Restore Defaults" button is included in the editor to easily revert to the standard dark theme.
- **Persistent User Data:** All user-generated files (Loadouts, Settings, custom Stratagems) are now stored in the user's `%APPDATA%` folder.
- This ensures that all user settings **will survive application updates** and will no longer be erased when installing a new version.

### ⚙️ Changed
- **Improved UI Safety:** The hotkey listener will now automatically deactivate whenever a loadout or hotkey setting is modified. The user is notified in the Activity Log and must reactivate, which guarantees the listener is always using the most current settings.
- **In-Depth User Guide:** The in-app Instructions have been completely rewritten into a comprehensive, step-by-step user guide covering all features.
- On first launch, the application now creates a personal, editable copy of the master stratagem list in the user's data folder.

---

## [2.1.0] - 2025-06-07

This version introduces professional user-facing features like automatic update checking and an integrated issue reporter, alongside critical stability fixes to the hotkey system.

### ✨ Added
- **Automatic Update Checker:** The application now checks for new versions on GitHub on startup and will notify the user with a pop-up if an update is available.
- **In-App Issue Reporter:** Added a "Submit an Issue" option to the Help menu. This feature opens a dialog for users to describe a bug or suggestion and then opens their browser to a pre-filled "New Issue" page on the public GitHub repository.
- **Comprehensive Numpad Support:** The application now correctly recognizes and handles hotkeys set to both the top number row and the Numpad, including operators (`+`, `-`, `*`, `/`, `.`) on the Numpad.

### 🐛 Fixed
- **Resolved Application Crash:** Fixed a critical crash on startup when using newer Python versions (3.13+) by establishing a stable Python 3.12 build environment.
- **Hotkey Listener Inconsistencies:** Corrected a deep bug in `pynput`'s key detection, ensuring key presses from all keyboard locations are recognized reliably.
- **Cleared "Ghost" Inputs:** Fixed a logic bug where the hotkey listener would not properly clear its state, sometimes causing macros to re-trigger unexpectedly.

---

## [2.0.0] - 2025-06-06

This release marks a complete, ground-up rewrite of the Stratagem Helper application, moving from a simple script to a full-featured, robust desktop application using the PyQt6 framework.

### 💥 Breaking Changes
- **Total Architectural Rewrite:** The application's entire codebase was replaced, moving from Tkinter to PyQt6. The new architecture is more stable, maintainable, and feature-rich.

### ✨ Added
- **Modern PyQt6 User Interface:** A new, professional, and responsive UI with a styled "card" layout.
- **Dark & Light Themes:** The application now supports switchable themes, accessible from the View menu.
- **Loadout System:** Users can now save and load complete configurations, including all hotkeys, stratagem choices, and timing settings. The most recent loadout is automatically loaded on startup.
- **Advanced Timing Controls:** A dedicated dialog allows users to fine-tune every aspect of the stratagem input simulation.
- **Dynamic Stratagem Slots:** Users can add or remove stratagem slots from the main window as needed.
- **Master Stratagem Editor:** A new dialog allows users to add, edit, or delete stratagems from the application's master list.
- **Visual Feedback:** Implemented a persistent "Activity Log" for detailed feedback and status icons to indicate configured slots.

### ⚙️ Changed
- Re-architected the entire hotkey system to use a more robust, threaded, string-based listener for maximum stability and key compatibility.

---

## [1.1.28 and Earlier] - The Original Tkinter Version

The initial releases of the Stratagem Helper were built as a lightweight and functional utility using Python's standard Tkinter framework. This version laid the groundwork for the core functionality of the application.

### ✨ Added
- **Core Functionality:** Basic system for executing stratagem codes via global hotkeys.
- **Simple GUI:** A user interface built with the Tkinter library, allowing users to see a predefined list of macros.
- **Hotkey Assignment:** Users could assign a keyboard hotkey to each stratagem in the list.
- **Configuration Saving:** Hotkey assignments could be saved to and loaded from a local `macros.json` file.
- **Activation Toggle:** A global toggle (using the Scroll Lock key) enabled or disabled the hotkey listener.
