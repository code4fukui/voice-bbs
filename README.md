# voice-bbs

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A minimalist voice-based bulletin board system powered by Deno.

This project is a simple, self-contained web application where users can post and listen to short voice messages. All data is stored locally in a `data.json` file.

## Features

-   **Voice Messaging**: Record and post voice messages directly from the browser.
-   **Playback**: Listen to messages posted by other users.
-   **Simple UI**: A clean, single-page interface styled with Sakura.css.
-   **Lightweight Backend**: A minimal Deno server handles API requests.
-   **Local Persistence**: Messages are saved in a local `data.json` file.

## How It Works

The application consists of a Deno server and a static frontend:
1.  The frontend uses the [`<input-voice>`](https://github.com/code4fukui/input-voice) web component to capture audio as a WAV file.
2.  When a user submits a post, the audio is Base64-encoded and sent to the `/api/add` endpoint.
3.  The Deno server appends the new post (name, audio data, timestamp) to `data.json`.
4.  On page load, the frontend fetches all posts from `/api/list` to display the message board.

## Prerequisites

-   [Git](https://git-scm.com/)
-   [Deno](https://deno.land/)

## Getting Started

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/code4fukui/voice-bbs.git
    ```

2.  **Navigate to the project directory:**
    ```bash
    cd voice-bbs
    ```

3.  **Start the server:**
    ```bash
    deno run -A --unstable voicebbs.js
    ```

4.  **Open the application:**
    Navigate to [http://localhost:8008](http://localhost:8008) in your web browser.

## API Endpoints

The server exposes two simple API endpoints:

-   `GET /api/list`
    -   Returns a JSON array of all post objects.
-   `POST /api/add`
    -   Accepts a JSON payload to add a new post.
    -   Payload format: `{ "name": "string", "wav": "base64-string", "date": "string" }`

Data is persisted in `data.json`, which is excluded from version control.

## Attribution

Created by [@taisukef](https://fukuno.jig.jp/3169) and provided under a CC BY license.