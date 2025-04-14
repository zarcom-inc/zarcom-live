<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Zarcom Live Stream</title>
  <style>
    body {
      margin: 0;
      background: #000;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    video {
      width: 90%;
      max-width: 800px;
      border: 4px solid #fff;
      border-radius: 10px;
    }
  </style>
</head>
<body>
  <video id="videoPlayer" controls autoplay muted playsinline>
    <source src="https://test-streams.mux.dev/x36xhzz/x36xhzz.m3u8" type="application/x-mpegURL" />
    Your browser does not support the video tag.
  </video>

  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
  <script>
    const video = document.getElementById('videoPlayer');
    const videoSrc = video.querySelector('source').src;
    if (Hls.isSupported()) {
      const hls = new Hls();
      hls.loadSource(videoSrc);
      hls.attachMedia(video);
    } else if (video.canPlayType('application/vnd.apple.mpegurl')) {
      video.src = videoSrc;
    }
  </script>
</body>
</html>
