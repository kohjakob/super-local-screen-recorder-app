# Screen Recorder

Single-file, browser-only screen recorder. Screen plus a draggable webcam bubble and microphone, in-browser trimming, MP4 download. Nothing is uploaded anywhere.

Everything lives in `index.html`: markup, styles and script. No build step, no dependencies. The only external request is the Nunito font from Google Fonts, and the page falls back to the system font when offline.

## Hosting

Upload `index.html` to any static host (GitHub Pages, Netlify, Cloudflare Pages, an S3 bucket, a plain web server). It must be served over HTTPS, since browsers only allow screen and camera capture on secure origins. `localhost` also counts as secure for local testing:

```sh
python3 -m http.server 8000
```

## Local use

The "Save recorder.html for later" button downloads the page itself as `recorder.html`. Double-clicking that file opens it from disk and it works the same way, offline.

## Browser support

Chrome, Edge and Safari record MP4 and get the trim editor. Firefox records WebM and downloads directly, because MediaRecorder WebM files carry no duration metadata and cannot be scrubbed.

Desktop only. Screen recording relies on the [Screen Capture API](https://developer.mozilla.org/docs/Web/API/Screen_Capture_API), which no mobile browser implements. Phones and tablets get a message pointing to a desktop browser instead.
