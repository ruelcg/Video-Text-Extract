## 📂 Downloading MP4 Files from SharePoint

To download an MP4 file hosted on SharePoint, use `yt-dlp` with the direct SharePoint video link:

```bash
yt-dlp -o "downloaded-video.mp4" <SHAREPOINT_VIDEO_URL>
```

If the file is protected by authentication, you may need to pass cookies:

1. Export cookies from your browser using an extension like [Get cookies.txt](https://chrome.google.com/webstore/detail/get-cookiestxt/lopibhbgjfmmjmbdgjcajdkdljkolmel).
2. Then run:

```bash
yt-dlp --cookies cookies.txt -o "downloaded-video.mp4" <SHAREPOINT_VIDEO_URL>
```

> ✅ Tip: SharePoint sometimes redirects or requires MFA — ensure you're logged in via your browser session before exporting cookies.

---

## 🧪 Generating Transcripts from MP4 Files

Once you have the `.mp4` file, you can generate a transcript using OpenAI’s Whisper or another speech-to-text tool. Here's how with Whisper:

1. Install Whisper:

```bash
pip install git+https://github.com/openai/whisper.git
```

2. Transcribe the file:

```bash
whisper downloaded-video.mp4 --model medium
```

This will create an `.srt`, `.txt`, and `.vtt` transcript alongside the audio.

> ⚠️ Whisper requires `ffmpeg`. If not installed, run:

```bash
brew install ffmpeg
```

---

## 📖 Viewing the Transcript

To read the subtitle file in the terminal:

```bash
cat "downloaded-video.srt"
```

To open it in a text editor:

```bash
open -a TextEdit "downloaded-video.srt"
```

---

## ⚠️ Notes

* SharePoint URLs may require authentication and expire — test with fresh links.
* Not all SharePoint videos have captions unless you generate them manually.
* Whisper supports multiple languages with different models: `base`, `small`, `medium`, and `large`.

---

## 📄 License

This script and documentation are provided under the [MIT License](LICENSE).

---

## 🙌 Acknowledgments

* [`yt-dlp`](https://github.com/yt-dlp/yt-dlp) for downloading video content.
* [`whisper`](https://github.com/openai/whisper) for transcription capabilities.
* [Get cookies.txt](https://chrome.google.com/webstore/detail/get-cookiestxt/lopibhbgjfmmjmbdgjcajdkdljkolmel) for exporting SharePoint session cookies.

