# TrackDrop

**TrackDrop** is a personal music mood tracker built as a full-stack demo app using Docker, PostgreSQL, Flask, and Google Cloud services. It lets users log and categorize songs by mood, track metadata, and visualize usage trends through cloud-powered analytics.

This project is designed to demonstrate backend development, containerization, Pub/Sub messaging, and cloud automation.

---

## Features

- Add, edit, view, and delete tracks with title, artist, mood, tags, and Spotify links
- Store data in a PostgreSQL database running in a Docker container
- Expose RESTful API endpoints via a Flask backend
- Automatically publish track events to Google Cloud Pub/Sub
- Trigger a Cloud Function to generate mood-based music stats
- GitHub CI/CD workflow with linting and future deploy hooks

---

## Tech Stack

- **Backend**: Python (Flask)
- **Database**: PostgreSQL (Docker)
- **Containerization**: Docker, Docker Compose
- **Cloud Services**:
  - Google Cloud Run (backend deployment)
  - Google Cloud Pub/Sub (event streaming)
  - Google Cloud Functions (background processing)
  - Optional: Google Cloud Storage (analytics output)
- **CI/CD**: GitHub Actions

---

## Architecture

