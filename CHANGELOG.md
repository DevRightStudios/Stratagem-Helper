# Changelog

All notable changes to this project will be documented in this file.
---

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
---

## [3.0.0] - 2025-07-05 - The Next-Generation Deployment

Greetings, Helldivers! This is a complete overhaul of the Stratagem Helper, rebuilt from the ground up on the new Flutter framework for enhanced performance, stability, and future readiness. This is a mandatory update for all personnel.

### ✨ Added
-   **Full Application Rewrite:** The entire application has been modernized on the Flutter platform.
-   **Stratagem Editor:** Full capability to Add, Edit, and Delete both stratagems and categories, including new sub-categories for enhanced organization.
-   **Advanced Loadout Manager:** Save, load, delete, and overwrite full loadouts, now including assigned hotkeys.
-   **Stratagem Trainer v2:** An immersive training simulator with three distinct modes:
    -   **Practice:** No-pressure drills with a shorter timer.
    -   **Standard:** Full-featured timed mode with dynamic scoring and time bonuses.
    -   **Scrambled:** An elite mode for veterans where codes are randomized and must be entered before they become unstable.
-   **Live Leaderboard:** A new screen to view top Helldiver scores, fetched directly from the Ministry of Truth's servers. Now includes patriot identification images.
-   **Automated Crash Reporter:** In the event of a critical malfunction, a separate utility will now launch to prepare a telemetry report for submission.
-   **Auto-Updater:** The application will now check for new versions on startup and prompt the user to install them.
-   **Sound Effects:** Added a full suite of audio feedback for UI interactions and trainer events to improve immersion.
-   **Data Versioning System:** A new system automatically updates stratagem data to the latest schematics from High Command while preserving user-created additions.

### 🐛 Fixed & Improved
-   **Complete Overhaul of Hotkey System:** Replaced the underlying hotkey and keystroke services to eliminate race conditions, preventing "stuck modifier key" bugs and improving stability.
-   **Application Shutdown:** Resolved a critical bug where the application process would not terminate correctly after closing the window. The app now shuts down cleanly.
-   **Server-Side Stability:** Rewrote and hardened all server-side API endpoints and file system permissions to resolve all `500 Internal Server Errors` and ensure reliable data handling.
-   **UI & Theme:** The entire user interface has been redesigned with a more consistent, modern, and themed look across all screens and dialogs.

---

## [2.5.2] - 2025-06-21

This is a hotfix release that adds a crucial user notification system for a legacy data bug and improves the stability of the settings manager.

### ✨ Added
- **Loadout Corruption Warning:** A new "Illuminate Infiltration" dialog will now appear on every launch if the application detects saved loadouts with missing timing data from a previous bug. The dialog now lists the specific loadouts that require fixing.

### 🐛 Fixed
- The "Edit/Save Loadout" dialog now correctly populates with default timing values instead of blank fields when creating a new loadout.
- Fixed a bug that could cause the "About" dialog to crash on open.

---

## [2.5.1] - 2025-06-21

This is a major stability and user experience hotfix that completely overhauls the loadout management system to resolve all known bugs related to saving and loading timing and key configurations.

### ✨ Added
- **Data Update Notifications:** The application will now show a "Ministry of Truth" themed pop-up on startup to inform users of any automatic corrections made to the master stratagem list, such as fixing incorrect input codes.

### ✨ Changed
- The "Configure Loadouts" and "Configure Timing/Key" dialogs have been removed and replaced with a single, powerful **"Manage Loadouts and Settings"** dialog.
- This new, unified manager provides a much clearer and more reliable workflow for editing the name, icon, and all associated settings for a saved loadout.

### 🐛 Fixed
- **CRITICAL:** Fixed a persistent bug where the "Tap/Hold" mode and "Stratagem Menu Key" settings would not save correctly to a loadout file.
- **CRITICAL:** Fixed a related bug where loading a saved loadout would fail to apply the correct "Tap/Hold" mode and other key settings.
- Resolved several `AttributeError` crashes that occurred when opening or interacting with the old loadout management dialogs.

---

## [2.5.0] - 2025-06-20

#### ✨ New Features

* **Quick Loadout Selection:** A new "Quick Loadout" dropdown menu and "Load" button have been added to the main "Hotkey Setup" tab. This provides users with a convenient way to apply a full loadout directly from the main screen.
    * The dropdown displays all saved loadouts with their assigned icons.
    * The "Load" button applies all settings from the selected loadout, including stratagem slots, timing, and key configurations.
    * The dropdown is automatically synchronized when loadouts are added, edited, or deleted.

#### 🐛 Bug Fixes

* **Fixed `AttributeError` in Loadout Manager:** Resolved a critical bug in the `LoadoutManagerDialog` where attempting to update a loadout's details would cause a crash. The method `_on_update_selected_details_clicked` was referencing UI elements (`edit_name_le`, `edit_icon_svg_combo`) with incorrect variable names. It now correctly uses `dialog_edit_name_le` and `dialog_edit_icon_svg_combo`.
* **Fixed `AttributeError` on Startup:** Corrected a startup crash caused by the `_populate_loadout_dropdown_qt` method being missing from the `MainWindow` class after a recent refactor. The method has been restored, allowing the application to initialize correctly.

#### ♻️ Code Refactoring

* Centralized loadout population logic by creating `_populate_main_loadout_combo` and ensuring it's called from all relevant update paths (`_load_initial_ui_state`, `_open_loadout_manager_dialog`, `_delete_selected_loadout_qt`, etc.) to maintain UI consistency.

---

## [2.4.3] - 2025-06-15

This is a critical hotfix patch that resolves major bugs related to the hotkey execution system, ensuring a stable and reliable experience for all users.

### 🐛 Fixed
- **CRITICAL:** Fixed a major bug that could cause the hotkey simulation to crash with a `ValueError` if timing or key settings were not properly loaded. The simulation is now significantly more robust.
- Fixed an issue where changes made to the "Stratagem Menu Key" in the configuration dialog were not being correctly applied, causing hotkeys to fail.
- The version number displayed in the main window's title bar now updates correctly with each new release.

---

## [2.4.2] - 2025-06-14

This is a hotfix release focused on significant visual polish for the Leaderboard and crucial bug fixes for improved stability and user experience.

### ✨ Changed
- The **Leaderboard** tab has been redesigned with a "card" style to visually match the rest of the application.
- The leaderboard table now has a polished "inset" look with proper borders, padding, and theme-aware colors.
- Improved the column spacing on the leaderboard for better readability.

### 🐛 Fixed
- The text color of scores on the leaderboard now updates immediately when the application theme is changed.
- The "Timing & Key Configuration" dialog will now correctly display default values if no settings have been previously saved.
- Fixed a critical bug that could cause the application to crash when opening the "About" dialog.

---

## [2.4.1] - 2025-06-14

This is a landmark update that officially launches the **Online Leaderboard** for the Stratagem Trainer! This release also includes major UI layout fixes and visual polish to enhance the user experience.

### ✨ Added
- **Online Leaderboard:** A new "Leaderboard" tab has been added to view top global scores from the DevRight Studios server.
- **Score Submission:** Players can now submit their scores from the "Timed Challenge" mode to compete for the top spot.
- **Player Personalization:** The application now prompts for a username on first launch, which is used for submissions and a new "Welcome" message.
- **Leaderboard Prestige:** The top 3 players are now highlighted with unique colors and medal icons (🥇, 🥈, 🥉) for recognition.

### ⚙️ Changed
- The main UI layout has been completely overhauled to resolve a long-standing bug that caused content to overlap or be hidden. The layout is now stable and robust.
- The "Activate Hotkeys" and "Add Slot" buttons have been permanently moved to a static area at the bottom of the "Hotkey Setup" tab for better accessibility.
- Improved the visual spacing and padding of the Stratagem Hotkey slots for better clarity.
- Improved the column spacing and data formatting on the Leaderboard table.

### 🐛 Fixed
- Resolved all connection issues related to SSL certificates and timeouts when communicating with the live server.
- Fixed a critical crash that occurred when submitting a score due to UI updates from a background thread.

---

## [2.4.0] - 2025-06-14

This release introduces significant new features, including a competitive **Leaderboard**, a **revamped Scoring System**, and a new **Username System**, alongside key bug fixes to enhance stability and user experience.

### ✨ Added
- A brand new global **Leaderboard System** to track and compare stratagem input speed and accuracy among players.
- A **Revamped Scoring System** for the stratagem trainer, offering more accurate and granular feedback on performance.
- A new **Username System** allowing players to set unique display names for the leaderboard and personalized experiences.

### ✨ Improvements
- Enhanced overall application performance and responsiveness.
- Improved user interface elements for a smoother experience.

### 🐛 Fixed
- Resolved an issue with the top grid layout not displaying correctly.
- Fixed a UI glitch affecting the "Activate Hotkeys" button.
- Addressed a bug where the trainer would stop recording scores under certain conditions.

---

## [2.3.1] - 2025-06-12

This is a stability patch that resolves numerous bugs and rendering issues related to the new theme system, greatly improving UI polish and reliability.

### 🐛 Fixed
- Fixed a major issue where the selected theme would not load correctly on application startup, often resulting in a visual mismatch until the theme was re-selected from the menu.
- Corrected a bug where stratagem slot icons (skulls) would not update their color when switching themes live.
- Overhauled the Light Theme styling to fix multiple visual bugs, including invisible checkboxes, improperly styled group boxes, and low-contrast borders.
- Restored the missing dropdown arrow icons for all `QComboBox` widgets.
- Fixed a crash (`NameError`) that could occur when opening the in-app User Guide.
- Improved the styling of the main tabs for better visual clarity on which tab is active.

---

## [2.3.0] - 2025-06-09

This is a massive feature release that introduces the **Stratagem Training Center**, a complete in-app game to help users improve their input speed and accuracy. It also adds the highly-requested ability to edit existing stratagems in the master list.

### ✨ Added
- A powerful **Stratagem Trainer** minigame accessible via a new "Stratagem Trainer" tab.
- The trainer includes multiple modes:
  - **Practice Mode:** For stress-free training with no timer.
  - **Timed Challenge:** A 30-second mode to test your speed, with scoring.
  - **Scrambled Codes:** An option for both modes that randomizes stratagem inputs.
- A **Time Bonus** system in Timed Challenge that rewards faster inputs with more time.
- An advanced **Re-scramble Mechanic** for the ultimate challenge, mirroring in-game effects.
- The ability to **edit** existing stratagems in the `Stratagems > Manage Master List` dialog, which opens a dedicated editor window.

### ⚙️ Changed
- The main window now uses a tabbed interface to separate "Hotkey Setup" and the new "Stratagem Trainer".
- The application's visual theme has been polished with improved tab styling and more distinct UI elements.

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

