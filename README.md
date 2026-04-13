# youtube-iframe-proxy

Static YouTube iframe proxy page for iOS/Capacitor apps that can hit YouTube player `Error 153` in WKWebView.

This repo hosts a single static page (`index.html`) that accepts query params and loads a YouTube `youtube-nocookie` embed URL.

## Why this exists

In some iOS WebView contexts, direct YouTube embeds can fail due to referrer/origin handling. A hosted proxy page is a lightweight workaround described here:

- [Fixing YouTube Error 153 in iOS Capacitor Apps](https://dev.to/davidvesely/fixing-youtube-error-153-in-ios-capacitor-apps-a-simple-proxy-solution-607)

## Usage

Host `index.html` on any static host, then open it like:

`https://your-domain.com/index.html?v=VIDEO_ID&autoplay=1&mute=1&loop=1&controls=0&fs=1`

- `v` (required): YouTube video ID
- `fs=1` (optional): enables fullscreen on the iframe
- Other query params are passed through to the YouTube embed URL
- `playsinline=1` is always forced by the proxy

## Embed example

```html
<iframe
  src="https://your-domain.com/index.html?v=dQw4w9WgXcQ&autoplay=1&mute=1&fs=1"
  allow="autoplay; encrypted-media"
></iframe>
```

## Deploy

Deploy this repo as static hosting (GitHub Pages, Netlify, Vercel static output, S3, etc.).