# Friendly Voice - AAC Communicator

## 🎯 What is "Friendly Voice"?

**Friendly Voice** is an Augmentative and Alternative Communication (AAC) application designed to empower non-verbal individuals, particularly children with autism or developmental delays, to communicate effectively. The app provides a highly customizable grid of buttons that, when tapped, speak words or phrases in both English and Egyptian Arabic.

The app focuses on simplicity, portability, and bilingual support, allowing users to build sentences, navigate through categories (folders), and personalize their communication board with their own photos and colors.

---

## 📱 Features Implemented

### 🎓 Interactive Onboarding
- **Hole-Punch Tutorial**: A guided tour for first-time users that highlights key interface elements using a spotlight effect.
- **Improved Tutorial Text**: Tutorial steps now feature clear, formatted text with bold titles and descriptive subtitles for better readability.
- **Guided Path**: Steps users through building sentences, interacting with buttons, using folders, and accessing settings.
- **Animated Demonstration**: The tutorial now includes a slow, smooth "flying" animation showing how to reorganize buttons using drag-and-drop.
- **Re-run Tutorial**: Users in trial mode can re-trigger the interactive tutorial at any time from the Settings screen.
- **Auto-Initialization**: On the very first launch, the app automatically extracts and loads a high-quality default vocabulary from a `vocab.fva.zip` asset, including custom pages and images.

### 🗣️ Bilingual Text-to-Speech (TTS)
- **Dual Language Support**: Seamless switching between English (US) and Egyptian Arabic (ar-EG).
- **Friendly Voice Names**: Technical system voice identifiers are mapped to human-readable labels like "Egypt - Female" or "United States - Male".
- **Dialect Identification**: Automatically detects and labels Arabic regional dialects (e.g., Gulf, Levant, Iraq, Egypt) from system voice metadata.
- **Alphabetical Sorting**: Voice options are organized alphabetically by country and gender for easy selection.
- **Speech Controls**: Adjustable speech rate (speed) and pitch to suit the user's preference.
- **Test Mode**: Built-in test button in settings to preview voice selections instantly.

### 🖼️ Customizable Communication Grid
- **Dynamic Buttons**: Add, edit, or delete buttons directly within the app.
- **Automatic Bilingual Translation**: While editing a button, typing a label in English automatically generates the Arabic translation (and vice versa) using **Google ML Kit**.
- **Drag-and-Drop Reorganization**: Double-tap any button to "lift" it, then drag and drop it onto another button to swap their positions instantly.
- **Personalized Visuals**: Support for custom images from the **Gallery**, **Camera**, or a built-in **AAC Symbol Search** (powered by ARASAAC).
- **Color Coding**: Pick from a curated palette of colors to categorize buttons (e.g., green for actions, yellow for feelings).
- **Button Text Font Size Control**: Choose between Small, Medium, or Large text for each button label.
- **Button Text Alignment**: Adjust the vertical alignment of the text to Top, Center, or Bottom.
- **Overlay Labels**: Smart text overlays ensure labels are readable even on top of custom photos.

### 📂 Page & Folder Navigation
- **Hierarchical Layout**: Create "Folders" that link to new pages, allowing for deep categorization of vocabulary.
- **Flexible Grids**: Configure different grid dimensions (2x2, 3x3, 4x4, etc.) for each individual page.
- **Smart Page Selection**: When managing or selecting pages, the page names are sorted and the "<New Page>" option is conveniently placed at the top of the list.
- **Navigation Controls**: Dedicated Home, Back, and Clear buttons for easy usage.

---

## 🏗️ Key Files & Responsibilities

### 📁 UI Layer (`com.aac.communicator.ui`)
- **`MainScreen.kt`**: The heart of the app. Handles the communication grid, the scrollable sentence bar, main navigation, and **drag-and-drop** swapping logic. Includes the automated tutorial demonstration logic.
- **`SettingsScreen.kt`**: Provides the interface for language selection, TTS adjustments, voice selection, monetization status, and data import/export. Includes a "Run Tutorial Again" feature for trial users.
- **`EditButtonScreen.kt`**: A comprehensive editor for individual buttons. Integrates **Google ML Kit Translate** for real-time bilingual label generation and ARASAAC symbol integration.
- **`TutorialOverlay.kt`**: Implements the "hole-punch" spotlight effect with enhanced, multi-styled text formatting for the interactive onboarding experience.

### 📁 Data Layer (`com.aac.communicator.data`)
- **`AppDatabase.kt`**: The Room database definition for storing `Page` and `CommunicationButton` entities.
- **`VocabInitializer.kt`**: Handles the critical first-run extraction of the `vocab.fva.zip` asset and populates the database.
- **`CommunicationRepository.kt`**: Manages data flow between the UI and the database, including the logic for vocabulary import/export transactions.
- **`SettingsManager.kt`**: Uses Jetpack DataStore to persist user preferences like language, speed, and selected voice.

### 📁 Services & Logic (`com.aac.communicator`)
- **`TTSService.kt`**: A wrapper around the Android TextToSpeech engine. Features advanced gender detection and dialect mapping to transform technical system strings into friendly labels.
- **`UpdateManager.kt`**: Handles the Google Play In-App Update flow, ensuring users are always on the latest version.
- **`TrialManager.kt`**: Manages the trial logic, interfacing with Firebase Firestore to track installation dates and premium status.
- **`MainActivity.kt`**: Handles the initial app state, including update checks, trial verification, initialization synchronization, and core app navigation.

---

## 👤 About the Author

**Tarek Radi** is the lead developer behind **Friendly Voice**. With a passion for creating accessible technology, Tarek built this app to provide a modern, user-friendly solution for the AAC community.

### 📩 Contact
For support, feedback, or inquiries, you can reach Tarek at:
- **Email**: [tarek.radi@gmail.com](mailto:tarek.radi@gmail.com)

---

**Version**: 1.0.13-Beta
**Last Updated**: 2025-02-15
