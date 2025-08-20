Google Slide Link: https://docs.google.com/presentation/d/1dATYm1yrSfuOOhjsbY7NciGavPl2XIwblP4ayyKrLrg/edit?usp=sharing

### 1. Problem Statement

In today's fast-paced digital world, mobile users rely heavily on screenshots to capture fleeting information—be it a meeting schedule, a purchase receipt, a recipe, or a spark of inspiration. However, this process is fundamentally broken:

* **Information Silos:** Screenshots are dumped into a chaotic, unorganized default photo gallery, mixed with personal photos.
* **Loss of Context:** The original thought or reason for capturing the screenshot is instantly lost. A picture of a flight itinerary is just an image without the context of "Book this for the family trip."
* **Inactionable Data:** The valuable text and data within these images remain locked and unsearchable. Finding a specific screenshot from months ago is a frustrating manual effort.
* **Privacy Concerns:** Existing solutions often rely on cloud uploads, creating privacy risks for sensitive information captured in screenshots.

**Essential Moments** addresses the critical gap between capturing information and making it truly useful, organized, and actionable, all while respecting user privacy.

---

### 2. Objectives

The primary objectives of the Essential Moments project are:

1.  **To Capture Effortlessly:** To create a frictionless system that automatically detects screenshots and allows users to add context (voice or text) in seconds.
2.  **To Organize Intelligently:** To build a smart, local-first "Vault" that automatically organizes and enriches captured "Moments" using AI for transcription and text recognition.
3.  **To Make Information Actionable:** To transform static images into dynamic data by extracting text, detecting intent, and integrating with system tools like the calendar for reminders and events.
4.  **To Champion Privacy-First Design:** To ensure the user is in complete control of their data by processing information on-device by default and requiring explicit consent for any cloud-based operations.

---

### 3. Tools and Techniques

| Category              | Technology / Tool        | Justification                                                                                             |
| --------------------- | ------------------------ | --------------------------------------------------------------------------------------------------------- |
| **Mobile Framework** | **React Native** | High-performance, native-feel cross-platform development from a single JavaScript codebase.               |
| **Native Bridge** | **Capacitor JS** | Provides robust access to native Android APIs, essential for our screenshot listener and overlay.          |
| **Local Database** | **RxDB (NoSQL)** | A fast, reactive, local-first database perfect for offline capabilities and future synchronization.       |
| **Dev Environment** | **Docker** | Ensures a consistent, isolated, and reproducible development environment for all team members.            |
| **Version Control** | **Git (GitFlow Model)** | A structured branching strategy for efficient multi-developer collaboration and stable releases.           |
| **On-Device AI** | **Google ML Kit** | Provides powerful, offline, on-device capabilities for OCR (Text Recognition) and Voice Transcription.    |
| **Cloud AI (Optional)**| **Gemini API** | Used for high-accuracy, user-initiated reprocessing of AI tasks and advanced visual search.               |
| **API Integration** | **Google Calendar API** | Enables seamless creation of calendar events and reminders directly from captured Moments.                 |

---
