# Nyaa.si Unofficial API

This document provides detailed documentation for the unofficial Nyaa.si API, which allows you to programmatically search for and retrieve entry information from the site.

## Base URL

The base URL for the API is: `https://kozynyaa-api.up.railway.app`

## Interactive Documentation

You can access the interactive API documentation at: [https://kozynyaa-api.up.railway.app/docs](https://kozynyaa-api.up.railway.app/docs)

---

## Endpoints

### Root

-   **GET /**
    -   **Description:** Returns a welcome message to confirm that the API is running.
    -   **Example Request:**
        ```bash
        curl -X 'GET' 'https://kozynyaa-api.up.railway.app/'
        ```
    -   **Example Response:**
        ```json
        {
          "message": "Welcome to the Nyaa.si API wrapper!"
        }
        ```

### Search

-   **GET /nyaa**
    -   **Description:** Searches for entries on Nyaa.si based on a query and optional filters.
    -   **Query Parameters:**
        -   `query` (string, **required**): The search term you want to look for.
        -   `filter` (string, optional): Filters the search results. Defaults to `no-filter`.
        -   `category` (string, optional): Narrows the search to a specific category. Defaults to `all`.
        -   `limit` (integer, optional): Limits the number of results returned.

    -   **Available Filters:**
        -   `no-filter`
        -   `no-remakes`
        -   `trusted-only`

    -   **Available Categories:**
        -   `all`
        -   `anime`
        -   `anime-amv`
        -   `anime-english-translated`
        -   `anime-non-english-translated`
        -   `anime-raw`
        -   `audio`
        -   `audio-lossless`
        -   `audio-lossy`
        -   `literature`
        -   `literature-english-translated`
        -   `literature-non-english-translated`
        -   `literature-raw`
        -   `live-action`
        -   `live-action-english-translated`
        -   `live-action-idol-pv`
        -   `live-action-non-english-translated`
        -   `live-action-raw`
        -   `pictures`
        -   `pictures-graphics`
        -   `pictures-photos`
        -   `software`
        -   `software-apps`
        -   `software-games`

    -   **Example Request (cURL):**
        ```bash
        curl -X 'GET' \
          'https://kozynyaa-api.up.railway.app/nyaa?query=one%20piece&filter=no-remakes&category=anime-english-translated&limit=5' \
          -H 'accept: application/json'
        ```

    -   **Example Request (Python):**
        ```python
        import requests

        url = "https://kozynyaa-api.up.railway.app/nyaa"
        params = {
            "query": "one piece",
            "filter": "no-remakes",
            "category": "anime-english-translated",
            "limit": 5
        }

        response = requests.get(url, params=params)
        print(response.json())
        ```

    -   **Example Response (JSON):**
        ```json
        [
          {
            "title": "[SubsPlease] One Piece - 1136 (1080p) [9547C1D0].mkv",
            "link": "https://nyaa.si/download/1992963.torrent",
            "guid": "https://nyaa.si/view/1992963",
            "pub_date": "Sun, 13 Jul 2025 15:47:12 -0000",
            "seeders": 1357,
            "leechers": 23,
            "downloads": 12805,
            "info_hash": "382613bed2096428fa090fbc32e503367ccd3ae2",
            "category_id": "1_2",
            "category": "Anime - English-translated",
            "size": "1.3 GiB",
            "comments": 0,
            "trusted": true,
            "remake": false
          }
        ]
