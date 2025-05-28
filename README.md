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

User Input --> Flask API (Cloud Run)
|
+--> PostgreSQL (Docker)
|
+--> Pub/Sub Topic: "track-events"
|
--> Cloud Function Subscriber
|
--> Stats JSON Output (GCS or API)


---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/trackdrop.git
cd trackdrop
```

### 2. Start Locally with Docker Compose

docker-compose up --build
  * Flask backend: localhost:5000
  * PostgreSQL: port 5432

### 3. Example API Requests

POST /tracks
{
  "title": "505",
  "artist": "Arctic Monkeys",
  "mood": "late night",
  "tags": ["indie", "nostalgic"],
  "spotify_url": "https://open.spotify.com/track/xyz"
}

GET /tracks → Returns list of all tracks
DELETE /tracks/{id} → Deletes a track

---

## Google Cloud Setup
### 1. Cloud Run
  * Deploy Flask app from Docker image
  * Expose endpoint for external usage

### 2. Pub/Sub
  * Create topic: track-events
  * Backend publishes message when tracks are added or updated

### 3. Cloud Function
  * Triggered by track-events
  * Reads DB or messages to generate summary
  * Saves or logs analytics

---

## GitHub Workflow
**.github/workflows/ci.yml**
Includes:
  * Linting (black, flake8)
  * Test placeholder
  * Future deployment hooks

---

## Example Mood Stats Output
{
  "top_mood": "chill",
  "mood_counts": {
    "chill": 8,
    "hype": 3,
    "sad": 2
  },
  "most_common_artist": "Clairo"
}

---

## Roadmap
  * Add basic frontend with React or HTML templates
  * Support track audio preview
  * Add authentication for multi-user support
  * Visualize mood stats in a dashboard
  * Auto-generate Spotify playlist link



