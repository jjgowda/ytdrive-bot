

# Advanced YouTube Downloader + Google Drive Uploader Bot

An **advanced Telegram bot** that downloads videos from YouTube (multi-quality, up to 1080p/full HD, audio-only, progress tracking) and uploads them directly to your Google Drive. Also supports direct file upload to Drive via Telegram.

## Features

- **YouTube video downloads:**  
  - Supports auto, 1080p, 720p, 480p, 360p, audio-only
  - Smart selection of best available quality
  - Merges video+audio when needed (FFmpeg auto-install)
- **Direct File Upload:**  
  - Send any document, audio, video, or photo to upload to Drive
- **Reatime Progress UI:**  
  - ETA, speed, size, progress bars for both download and upload
- **Google Drive Upload:**  
  - Auth via personal OAuth or service account
  - Uploads to root or specific folder
- **All-in-one deployment:**  
  - Cloud-ready (e.g. Railway, Render) or local (ensure FFmpeg & Python 3.10+)

## Setup

### 1. Clone

```bash
git clone https://github.com/yourusername/ytdrive-bot.git
cd ytdrive-bot
```

### 2. Install Dependencies

Create a virtualenv (recommended), then:

```bash
pip install -r requirements.txt
```

Minimum `requirements.txt`:
```
pyrogram>=2.0.106
tgcrypto>=1.2.5
google-api-python-client>=2.118.0
google-auth>=2.29.0
google-auth-httplib2>=0.2.0
google-auth-oauthlib>=1.2.0
python-dotenv>=1.0.1
yt-dlp>=2024.1.7
```

### 3. Register Telegram & Google Apps

- **Telegram:** [Register a bot](https://my.telegram.org)
  - Set `APP_ID`, `API_HASH`, `BOT_TOKEN` in `.env`

- **Google OAuth:** [Create OAuth credentials](https://console.developers.google.com/)
  - Set `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET` in `.env`
  - Use [OAuth Playground](https://developers.google.com/oauthplayground) to get `OAUTH_TOKEN` & `OAUTH_REFRESH_TOKEN`
  - Optional: `DRIVE_FOLDER_ID` to upload in a specific Drive folder

Example `.env`:
```
APP_ID=123456
API_HASH=yourhash
BOT_TOKEN=token:abc
GOOGLE_CLIENT_ID=...
GOOGLE_CLIENT_SECRET=...
OAUTH_TOKEN=...
OAUTH_REFRESH_TOKEN=...
DRIVE_FOLDER_ID= (optional)
```

### 4. Run the Bot

```bash
python bot.py
```

First run will validate FFmpeg and OAuth tokens.

***

## Usage

**On Telegram:**

- **Download Any YouTube Video (Best/Auto Quality):**  
  Send the link:  
  ```
  https://youtube.com/watch?v=example
  ```
- **Force 1080p or other quality:**  
  ```
  /yt 1080p <youtube-url>
  /yt 720p <youtube-url>
  /ytaudio <youtube-url>   # Audio only
  ```
- **Upload any file to Drive:**  
  Send a file as document, audio, video, or photo

- **Progress, quality, ETA, Drive link shown in chat!**

***

## Troubleshooting

- **OAuth error:** Use Google OAuth Playground for token refresh, review error logs in console.
- **FFmpeg errors:** Bot tries to install FFmpeg (Ubuntu/Cloud); ensure it's available if using Windows.
- **Download failed:** Make sure `yt-dlp` is up-to-date, quality exists for video.

***

## License

MIT — Free to use, modify, distribute with attribution.

***

**Made with ❤️ by Jeevan Gowda.**

***

Let me know if you want to add badges, contributing instructions, or a usage GIF!
