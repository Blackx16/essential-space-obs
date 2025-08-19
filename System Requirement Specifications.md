---
title: System Requirement Specifications
date: 2025-08-17
draft: false
tags:
  - srs
  - checkpoint
---
### 1. Introduction
1. **Purpose**:
		The purpose of this Software Requirements Specification (SRS) is to provide a detailed description of the requirements for the Essential Moments application. This document outlines the functional and non-functional requirements for the app, serving as the foundational agreement between stakeholders and the development team to guide the design, development, and testing of the system.
		
2. **Scope**:
		This system is an intelligent mobile companion designed to capture, organize, and make actionable the fleeting ideas and information users save via screenshots. It will automate the process of screenshot capture, enrich it with notes and voice memos, and use on-device and cloud-based AI to extract meaningful data. The goal is to replace the disorganized, default phone gallery with a smart, private, and actionable "second brain".
		
3. **Audience**:
	This SRS document is intended for a diverse audience, including: 
	- Faculty Mentor: To give a clear idea reference for the project.
	- Developers & Testers: To use as a definitive guide for building and verifying the software.
	- Project Manager: To oversee the project and ensure all requirements are met.
	- UI/UX Designers: To understand the functional flow and user interaction points.
	- Stakeholders: To have a clear reference for the agreed-upon scope and functionality.


### 2. Overall Description

1. **Product Perspective**
	Essential Moments will be a standalone native Android application built using modern web-native technologies (React Native with Capacitor). It is designed as a user-centric, privacy-first tool that functions primarily offline. While it leverages external APIs (Google ML Kit, Gemini, Google Calendar) to enhance functionality, its core value is delivered on-device.
	
2. **Functions**
	The primary functions of the system include:
	- ***Screenshot Detection***: Automatically detecting when a user takes a screenshot.
	- ***Moment Creation***: Allowing users to instantly attach text or voice notes to a new screenshot.
	- ***The Vault***: A local-first, secure database for storing all Moments.
	- ***Essential Space***: A gallery and workspace to view, edit, and interact with saved Moments.
	- ***AI Processing***: Using Machine Learning to transcribe audio, extract text from images (OCR), and detect user intent.
	- **Calendar Integration**: Creating calendar events and reminders based on detected intent.
	
3. **Constraints**
	- The application will be developed for the Android platform only in its initial version.
	- The system requires user-granted permissions to read storage (for screenshots) and display over other apps (for the pop-up).
	- Certain AI and scheduling features require an internet connection and user authentication with Google services.
	- All data is stored locally by default. Any action that sends data to a cloud service (e.g., Gemini API) requires explicit user consent.

4. **Assumptions**
	- It is assumed that users will have a device running a modern version of Android.
	- Users have a Google account for calendar integration and optional cloud-based AI features.
	- Users will have basic familiarity with mobile application usage and granting permissions.


### 3.  Specific Requirements

1. Functional Requirements
- ***FR-1: Screenshot Detection & Overlay***
	- The system shall run a persistent foreground service to monitor for new screenshots.
	- Upon detection of a new screenshot, the system shall display a subtle, non-intrusive, tappable overlay button on the screen.
	- Tapping the overlay button shall initiate the "Moment Creation" flow.
- ***FR-2: Moment Creation***
	- The system shall provide an interface to view the newly captured screenshot.
	- The interface shall allow the user to add a text note, record a voice memo, or both.
	- The system shall save the screenshot and any associated notes as a single "Moment" entity in the local Vault.
- ***FR-3: Essential Space (Gallery & Workspace)***
	- The system shall provide a central gallery view, the "Essential Space," to display all saved Moments.
	- Users shall be able to tap on any Moment to open a detailed view.
	- In the detailed view, users shall be able to edit text notes, play voice memos, and add further annotations.
	- The system shall provide tools for drawing or annotating directly on the screenshot.
- ***FR-4: The Vault (Local Storage)***
	- The system shall use a local-first NoSQL database (RxDB) to store all user data.
	- Each Moment shall be stored as a flexible document containing the image path, text notes, audio path, metadata, and timestamps.
	- All data must be stored exclusively on the user's device unless an explicit cloud action is taken.
- ***FR-5: AI Processing*** 
	- *(Local)*: The system shall use the on-device Google ML Kit to automatically transcribe voice memos into text.
	- (*Local)*: The system shall use the on-device Google ML Kit to perform Optical Character Recognition (OCR) on screenshots to extract text.
	- *(Cloud)*: The system shall offer an option for the user to manually trigger reprocessing of a voice memo or OCR task using the more powerful Gemini API for higher accuracy. This action must require user consent.
- ***FR-6: Calendar Integration***
	- The system shall analyze transcribed text (from voice or OCR) to detect intent related to dates, times, or events (e.g., "Meeting at 4 PM").
	- If scheduling intent is detected, the system shall prompt the user with a suggestion to create a calendar event.
	- Upon user confirmation, the system shall use the Google Calendar API to pre-fill and create a new calendar event.
	
2. **Non-Functional Requirements**
- ***NFR-1: Performance*** 
	- The screenshot detection overlay shall appear within 1 second of a screenshot being taken.
	- The application's UI shall be responsive, with screen transitions and data loading completing in under 2 seconds on a mid-range device.
	- On-device AI processing (transcription, OCR) should complete within 5-10 seconds for typical inputs.
- ***NFR-2: Usability*** 
	- The system shall have a clean, intuitive interface that adheres to Google's Material Design principles.
	- The workflow for creating a Moment shall be fast and require minimal taps.
	- The system shall provide clear feedback for all actions (e.g., "Moment saved," "Transcription complete").
- ***NFR-3: Security*** 
	- All user data must be stored locally on the device's sandboxed storage.
	- No data shall be uploaded to any cloud service automatically. Every cloud-based action must be user-initiated and require explicit consent.
	- API keys and sensitive credentials must be stored securely and not be exposed in the application code.
- ***NFR-4: Reliability*** 
	- The core functionality (screenshot capture, note-taking, local storage) shall be fully operational offline.
	- The foreground service for screenshot detection must be stable and restart automatically if terminated by the OS.
	- The system must handle permissions gracefully, guiding the user to grant necessary permissions if they are denied.
- ***NFR-5: Maintainability*** 
	- The system's code shall be modular, well-documented, and structured to allow for easy troubleshooting and future enhancements.
	- The project will follow the GitFlow branching model to ensure code stability.


### 4. Use Cases
**Actor: User**
	
- **Use Case:** ***Effortless Idea Capture***
	- **Description:** The User sees something interesting online and takes a screenshot. The Essential Moments overlay appears. The User taps it, records a quick voice memo saying "Follow up on this marketing idea tomorrow afternoon," and saves the Moment. The entire interaction takes less than 15 seconds.
	
- **Use Case:** ***Scheduling a Meeting from an Image***
	- **Description:** The User takes a screenshot of a meeting invitation in an email. They open the Moment in the Essential Space. The on-device OCR has already extracted the text "Board meeting, Friday at 3 PM". The app shows a suggestion chip: "Create Calendar Event". The User taps it, confirms the details, and the event is added to their Google Calendar.
		
- **Use Case:** ***Reviewing and Organizing Ideas***
	- **Description:** The User opens the Essential Space to review their week's Moments. They find a screenshot of a book recommendation. The voice memo they left has been transcribed. They add a text note "Buy this for Sarah's birthday" and use the annotation tool to circle the author's name on the image.