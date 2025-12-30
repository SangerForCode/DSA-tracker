# Live Collaborative DSA Course Tracker

## Project Aim
This project is a feature-rich, real-time web application for tracking progress through the popular "Striver's A2Z" Data Structures and Algorithms course. It functions as a live, collaborative dashboard where multiple users can simultaneously view and update progress, making it an ideal tool for study groups or mentorship.

## Technical Implementation
This application is uniquely architected as a "zero-build" single-page application contained entirely within an `index.html` file. It uses an unconventional but effective stack:
- **React and JSX** are rendered directly in the browser, with in-browser compilation handled by the Babel Standalone CDN.
- **Dependencies** like React, ReactDOM, and Lucide-React icons are loaded from an ES Module CDN (`esm.sh`).
- **Real-time backend** is powered by Google Firebase (Firestore), enabling live data synchronization across all connected clients.
- **Styling** is achieved with Tailwind CSS, loaded via a CDN.

This setup creates a powerful, serverless frontend that is easy to deploy and share.

## Key Features
- **Collaborative Real-Time Sync:** All progress, confidence ratings, and notes are shared and updated live for all users.
- **Detailed Progress Tracking:** Users can check off videos, rate their confidence on a 5-star scale, and mark topics for future revisits.
- **Intelligent Pacing:** A dynamic dashboard calculates if the user is on track, ahead, or behind a configurable study schedule (e.g., complete in 5 months).
- **Per-Video Community Notes:** A modal-based discussion board allows users to share notes and ask questions on each specific video, with all comments synced live.
- **Phase-Based Roadmap:** Organizes the entire course into a clear, multi-phase roadmap with defined goals and exit criteria for each stage.

## Setup Instructions
- **Prerequisite:** Requires a Google Firebase project with Firestore and Anonymous Authentication enabled.
- **Configuration:** Edit the `index.html` file and replace the placeholder `firebaseConfig` object with your own Firebase project credentials.
- **Run:** Open the `index.html` file in a web browser.

## System Diagram
```mermaid
flowchart TD
    subgraph "Clients"
        A[User's Browser]
        B[Collaborator's Browser]
    end

    subgraph "Frontend (Zero-Build)"
        C(index.html)
        D{React App (via CDN)};
        E{Babel.js (CDN for JSX)};
        F{Tailwind CSS (CDN)};
    end

    subgraph "Backend"
        G[(Firebase: Firestore & Auth)];
    end

    A -- Loads --> C;
    B -- Loads --> C;

    C -- Contains & Runs --> D;
    D -- Compiled by --> E;
    D -- Styled by --> F;
    
    D -- Reads/Writes Data --> G;
    G -- Real-time Sync --> D;
```