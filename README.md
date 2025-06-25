# 🎠 Extracting YouTube Transcripts via Command Line on macOS

This guide describes how to extract subtitles or transcripts from a YouTube video using the command line on macOS. It uses [`yt-dlp`](https://github.com/yt-dlp/yt-dlp), a powerful command-line tool for downloading YouTube content and metadata.

---

## 📅 Installation

First, ensure you have [Homebrew](https://brew.sh/) installed:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then install `yt-dlp`:

```bash
brew install yt-dlp
```

---

## 📜 Downloading the Transcript

Use the following command to download auto-generated subtitles (if available) **without downloading the video**:

```bash
yt-dlp --write-auto-sub --skip-download --sub-format "srt" --output "%(title)s.%(ext)s" <YOUTUBE_VIDEO_URL>
```

### 🔍 Command Breakdown

* `--write-auto-sub`: Downloads YouTube's automatically generated subtitles.
* `--skip-download`: Skips downloading the video itself.
* `--sub-format "srt"`: Downloads subtitles in `.srt` format (you can also use `vtt`).
* `--output "%(title)s.%(ext)s"`: Saves the file using the video title.
* `<YOUTUBE_VIDEO_URL>`: Replace this with the actual YouTube video URL.

---

## 📂 Example Output

If the video is titled `Exploring the Ocean`, the resulting subtitle file might be:

```text
Exploring the Ocean.en.srt
```

---

## 📖 Viewing the Transcript

To read the subtitle file in the terminal:

```bash
cat "Exploring the Ocean.en.srt"
```

To open the subtitle file in a macOS text editor:

```bash
open -a TextEdit "Exploring the Ocean.en.srt"
```

---

## 📌 Optional: Download Manually Uploaded Subtitles

If the video has professionally added subtitles, use:

```bash
yt-dlp --write-sub --skip-download --sub-format "srt" <YOUTUBE_VIDEO_URL>
```

To specify a subtitle language (e.g., English):

```bash
yt-dlp --write-sub --sub-lang en --skip-download <YOUTUBE_VIDEO_URL>
```

---

## 💪 Quick Test Example

Test the process on a known video with subtitles:

```bash
yt-dlp --write-auto-sub --skip-download https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

---

## ⚠️ Notes

* Not all videos provide auto-generated or manual subtitles.
* You can convert `.srt` files to plain text or use them with video players.
* `yt-dlp` is a more up-to-date alternative to `youtube-dl`.

---

## 📄 License

This script and documentation are provided under the [MIT License](LICENSE).

---

## 🙌 Acknowledgments

* [`yt-dlp`](https://github.com/yt-dlp/yt-dlp) for making YouTube scraping accessible and open source.
