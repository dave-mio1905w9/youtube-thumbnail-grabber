# youtube-thumbnail-grabber

I needed a quick way to bulk-download high-resolution thumbnails for archives and video analysis without dealing with the slow, quota-limited official YouTube API. This tool grabs the best available thumbnail for a given video, playlist, or channel URL by parsing the public pages directly.

It handles parallel downloads for playlists, falls back gracefully through resolution tiers (from `maxresdefault` down to `default`), and names files cleanly based on video IDs.

## Installation

Clone the repository and install the single dependency:

```bash
pip install -r requirements.txt
```

## Usage

Pass a video, playlist, or channel URL to the script. By default, it saves files in a `thumbnails` directory in the current folder.

### Save a single video thumbnail

```bash
python grabber.py https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

### Save all thumbnails from a playlist in parallel

```bash
python grabber.py https://www.youtube.com/playlist?list=PLBCF293021EB61A4E --output ./my-playlist-art
```

### Limit parallel workers and force overwrite

```bash
python grabber.py https://www.youtube.com/playlist?list=PLBCF293021EB61A4E -w 4 --overwrite
```

Options:
* `-o, --output`: Directory to save thumbnails (created if it doesn't exist).
* `-w, --workers`: Number of concurrent download workers for playlists (default: 8).
* `--overwrite`: Overwrite existing files instead of skipping them.

<!-- verified: 2026-09-21 -->
