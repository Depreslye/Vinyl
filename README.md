<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Vinyl Player</title>

  <!-- Spotify iFrame API -->
  <script src="https://open.spotify.com/embed/iframe-api/v1" async></script>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      min-height: 100vh;
      background:
        radial-gradient(circle at 20% 20%, #242424 0%, transparent 35%),
        radial-gradient(circle at 80% 80%, #151515 0%, transparent 40%),
        #080808;

      color: white;
      font-family: Arial, Helvetica, sans-serif;

      display: flex;
      align-items: center;
      justify-content: center;

      overflow-x: hidden;
    }

    .app {
      width: min(1200px, 94vw);
      min-height: 700px;

      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 35px;

      padding: 35px;

      background: rgba(20, 20, 20, 0.82);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 28px;

      box-shadow:
        0 30px 80px rgba(0,0,0,0.65),
        inset 0 0 40px rgba(255,255,255,0.015);

      backdrop-filter: blur(20px);
    }

    /* =========================
       LEFT - SPOTIFY
    ========================= */

    .spotify-section {
      display: flex;
      flex-direction: column;
      justify-content: center;

      min-width: 0;
    }

    .title {
      margin-bottom: 20px;
    }

    .title h1 {
      font-size: 32px;
      letter-spacing: -1px;
    }

    .title p {
      margin-top: 7px;
      color: #999;
      font-size: 14px;
    }

    #embed-iframe {
      width: 100%;
      min-height: 600px;

      border-radius: 18px;
      overflow: hidden;
    }

    /* =========================
       RIGHT - VINYL
    ========================= */

    .vinyl-section {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;

      position: relative;
    }

    .turntable {
      width: min(470px, 80vw);
      aspect-ratio: 1;

      display: flex;
      align-items: center;
      justify-content: center;

      position: relative;

      border-radius: 30px;

      background:
        linear-gradient(
          145deg,
          #181818,
          #0b0b0b
        );

      box-shadow:
        inset 0 0 50px rgba(0,0,0,0.8),
        0 25px 60px rgba(0,0,0,0.6);
    }

    /* =========================
       VINYL DISC
    ========================= */

    .vinyl {
      width: 78%;
      aspect-ratio: 1;

      border-radius: 50%;

      position: relative;

      background:
        repeating-radial-gradient(
          circle,
          #050505 0px,
          #111 2px,
          #050505 4px,
          #090909 6px
        );

      box-shadow:
        0 15px 35px rgba(0,0,0,0.8),
        inset 0 0 25px rgba(255,255,255,0.04);

      animation: spin 4s linear infinite;
      animation-play-state: paused;

      transition: transform 0.4s ease;
    }

    .vinyl.playing {
      animation-play-state: running;
    }

    @keyframes spin {
      from {
        transform: rotate(0deg);
      }

      to {
        transform: rotate(360deg);
      }
    }

    /* Vinyl grooves */

    .vinyl::before {
      content: "";

      position: absolute;
      inset: 5%;

      border-radius: 50%;

      background:
        repeating-radial-gradient(
          circle,
          transparent 0px,
          transparent 3px,
          rgba(255,255,255,0.035) 4px,
          transparent 5px
        );

      pointer-events: none;
    }

    /* =========================
       LABEL
    ========================= */

    .label {
      position: absolute;

      width: 31%;
      aspect-ratio: 1;

      left: 50%;
      top: 50%;

      transform: translate(-50%, -50%);

      border-radius: 50%;

      background:
        radial-gradient(
          circle,
          #444 0%,
          #222 45%,
          #111 100%
        );

      border: 2px solid rgba(255,255,255,0.12);

      display: flex;
      align-items: center;
      justify-content: center;

      box-shadow:
        inset 0 0 20px rgba(0,0,0,0.6);
    }

    .label-text {
      text-align: center;

      font-size: clamp(8px, 1.2vw, 13px);
      font-weight: bold;

      letter-spacing: 2px;

      color: #ddd;

      text-transform: uppercase;
    }

    /* Center hole */

    .hole {
      position: absolute;

      width: 9px;
      height: 9px;

      left: 50%;
      top: 50%;

      transform: translate(-50%, -50%);

      border-radius: 50%;

      background: #050505;

      box-shadow:
        0 0 0 2px rgba(255,255,255,0.12);
    }

    /* =========================
       STATUS
    ========================= */

    .status {
      margin-top: 28px;

      display: flex;
      align-items: center;
      gap: 10px;

      color: #888;

      font-size: 13px;
      letter-spacing: 1px;

      text-transform: uppercase;
    }

    .status-dot {
      width: 9px;
      height: 9px;

      border-radius: 50%;

      background: #555;

      transition:
        background 0.3s ease,
        box-shadow 0.3s ease;
    }

    .playing-status .status-dot {
      background: #1ed760;

      box-shadow:
        0 0 10px #1ed760;
    }

    .playing-status {
      color: #1ed760;
    }

    /* =========================
       DECORATION
    ========================= */

    .shine {
      position: absolute;

      width: 35%;
      height: 35%;

      border-radius: 50%;

      background: radial-gradient(
        circle,
        rgba(255,255,255,0.12),
        transparent 70%
      );

      top: 10%;
      left: 15%;

      pointer-events: none;
    }

    .footer {
      position: absolute;

      bottom: 15px;

      width: 100%;

      text-align: center;

      color: #444;

      font-size: 11px;

      letter-spacing: 1px;
    }

    /* =========================
       MOBILE
    ========================= */

    @media (max-width: 850px) {

      body {
        padding: 20px 0;
      }

      .app {
        grid-template-columns: 1fr;

        width: 94vw;

        padding: 22px;

        gap: 35px;
      }

      .spotify-section {
        order: 2;
      }

      .vinyl-section {
        order: 1;
      }

      .turntable {
        width: min(390px, 82vw);
      }

      #embed-iframe {
        min-height: 600px;
      }

      .title h1 {
        font-size: 25px;
      }
    }
  </style>
</head>

<body>

  <main class="app">

    <!-- =========================
         SPOTIFY
    ========================== -->

    <section class="spotify-section">

      <div class="title">
        <h1>My Playlist</h1>
        <p>Play something and watch the vinyl spin.</p>
      </div>

      <div id="embed-iframe"></div>

    </section>


    <!-- =========================
         VINYL
    ========================== -->

    <section class="vinyl-section">

      <div class="turntable">

        <div class="shine"></div>

        <div class="vinyl" id="vinyl">

          <div class="label">
            <div class="label-text">
              Spotify<br>
              Vinyl
            </div>
          </div>

          <div class="hole"></div>

        </div>

      </div>


      <div class="status" id="status">

        <span class="status-dot"></span>

        <span id="statusText">
          Paused
        </span>

      </div>

    </section>

  </main>


  <div class="footer">
    VINYL PLAYER • SPOTIFY
  </div>


  <script>

    /*
      ==========================================
      SPOTIFY PLAYLIST
      ==========================================
    */

    const playlistURL =
      "https://open.spotify.com/playlist/0aFukFImzZqlBhQzskT2T3";


    /*
      ==========================================
      ELEMENTS
      ==========================================
    */

    const vinyl =
      document.getElementById("vinyl");

    const status =
      document.getElementById("status");

    const statusText =
      document.getElementById("statusText");


    /*
      ==========================================
      VINYL CONTROLS
      ==========================================
    */

    function startVinyl() {

      vinyl.classList.add("playing");

      status.classList.add("playing-status");

      statusText.textContent = "Playing";

    }


    function stopVinyl() {

      vinyl.classList.remove("playing");

      status.classList.remove("playing-status");

      statusText.textContent = "Paused";

    }


    /*
      ==========================================
      SPOTIFY IFRAME API
      ==========================================
    */

    window.onSpotifyIframeApiReady = (IFrameAPI) => {

      const element =
        document.getElementById("embed-iframe");


      const options = {

        width: "100%",

        height: "600",

        url: playlistURL

      };


      IFrameAPI.createController(
        element,
        options,

        (EmbedController) => {

          /*
            When Spotify starts a track
          */

          EmbedController.addListener(
            "playback_started",
            () => {

              startVinyl();

            }
          );


          /*
            Whenever playback state changes
          */

          EmbedController.addListener(
            "playback_update",
            (event) => {

              if (!event || !event.data) {
                return;
              }


              if (event.data.isPaused) {

                stopVinyl();

              } else {

                startVinyl();

              }

            }
          );


          /*
            Embed is ready
          */

          EmbedController.addListener(
            "ready",
            () => {

              console.log(
                "Spotify player ready."
              );

            }
          );

        }
      );

    };

  </script>

</body>
</html>
