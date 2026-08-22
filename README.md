<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Spotify Vinyl</title>

<!-- Spotify iFrame API -->
<script src="https://open.spotify.com/embed/iframe-api/v1" async></script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    min-height: 100vh;

    background:
        radial-gradient(circle at 20% 20%, #292929, transparent 35%),
        radial-gradient(circle at 80% 80%, #151515, transparent 40%),
        #050505;

    color: white;

    font-family: Arial, Helvetica, sans-serif;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 25px;
}

/* =========================
   CONTENEDOR
========================= */

.container {
    width: min(1200px, 100%);

    min-height: 680px;

    display: grid;
    grid-template-columns: 1fr 1fr;

    gap: 35px;

    padding: 30px;

    background: rgba(18,18,18,.94);

    border: 1px solid rgba(255,255,255,.08);

    border-radius: 25px;

    box-shadow:
        0 30px 80px rgba(0,0,0,.75),
        inset 0 0 40px rgba(255,255,255,.02);
}

/* =========================
   SPOTIFY
========================= */

.spotify {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.header {
    margin-bottom: 18px;
}

.header h1 {
    font-size: 30px;
    letter-spacing: -1px;
}

.header p {
    margin-top: 6px;
    color: #888;
    font-size: 14px;
}

/*
   IMPORTANTE:
   Este DIV será reemplazado
   automáticamente por Spotify.
*/

#spotify-player {
    width: 100%;
    min-height: 600px;

    border-radius: 18px;

    overflow: hidden;
}

/* =========================
   VINILO
========================= */

.vinyl-area {
    display: flex;
    flex-direction: column;

    justify-content: center;
    align-items: center;
}

.turntable {
    width: min(450px, 80vw);

    aspect-ratio: 1;

    position: relative;

    display: flex;
    justify-content: center;
    align-items: center;

    border-radius: 30px;

    background:
        linear-gradient(
            145deg,
            #1d1d1d,
            #080808
        );

    box-shadow:
        0 25px 60px rgba(0,0,0,.75),
        inset 0 0 40px rgba(0,0,0,.8);
}

/* =========================
   DISCO
========================= */

.vinyl {
    width: 78%;
    aspect-ratio: 1;

    position: relative;

    border-radius: 50%;

    background:
        repeating-radial-gradient(
            circle,
            #030303 0px,
            #111 2px,
            #050505 4px,
            #0b0b0b 6px
        );

    box-shadow:
        0 20px 40px rgba(0,0,0,.85),
        inset 0 0 30px rgba(255,255,255,.05);

    /*
       AQUÍ ESTÁ LA ANIMACIÓN
    */

    animation:
        spin 4s linear infinite;

    animation-play-state: paused;

    transition:
        filter .3s ease;
}

/* GIRANDO */

.vinyl.playing {
    animation-play-state: running;

    filter:
        brightness(1.08);
}

/* =========================
   ANIMACIÓN
========================= */

@keyframes spin {

    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(360deg);
    }

}

/* =========================
   REFLEJO
========================= */

.vinyl::before {

    content: "";

    position: absolute;

    inset: 0;

    border-radius: 50%;

    background:
        linear-gradient(
            135deg,
            rgba(255,255,255,.10),
            transparent 25%,
            transparent 70%,
            rgba(255,255,255,.03)
        );

    pointer-events: none;
}

/* =========================
   LABEL
========================= */

.label {

    position: absolute;

    width: 32%;
    aspect-ratio: 1;

    left: 50%;
    top: 50%;

    transform:
        translate(-50%, -50%);

    border-radius: 50%;

    background:
        radial-gradient(
            circle,
            #666,
            #292929 55%,
            #111
        );

    border:
        2px solid rgba(255,255,255,.12);

    display: flex;

    justify-content: center;
    align-items: center;

    text-align: center;

    box-shadow:
        inset 0 0 20px rgba(0,0,0,.7);
}

.label span {

    font-size: 11px;

    font-weight: bold;

    letter-spacing: 2px;

    color: #ddd;
}

/* =========================
   CENTRO
========================= */

.hole {

    position: absolute;

    width: 9px;
    height: 9px;

    left: 50%;
    top: 50%;

    transform:
        translate(-50%, -50%);

    border-radius: 50%;

    background: #050505;

    box-shadow:
        0 0 0 2px rgba(255,255,255,.1);
}

/* =========================
   BRAZO
========================= */

.arm {

    position: absolute;

    width: 42%;
    height: 8px;

    right: 3%;
    top: 16%;

    background: #777;

    border-radius: 10px;

    transform: rotate(25deg);

    transform-origin: right center;

    box-shadow:
        0 4px 10px rgba(0,0,0,.7);
}

.arm::after {

    content: "";

    position: absolute;

    right: -4px;
    top: -4px;

    width: 16px;
    height: 16px;

    border-radius: 50%;

    background: #aaa;
}

/* =========================
   ESTADO
========================= */

.status {

    margin-top: 25px;

    display: flex;

    align-items: center;

    gap: 10px;

    color: #777;

    font-size: 13px;

    letter-spacing: 1px;

    text-transform: uppercase;
}

.dot {

    width: 9px;
    height: 9px;

    border-radius: 50%;

    background: #555;

    transition:
        background .3s ease,
        box-shadow .3s ease;
}

.status.playing {

    color: #1ed760;
}

.status.playing .dot {

    background: #1ed760;

    box-shadow:
        0 0 12px #1ed760;
}

/* =========================
   MOBILE
========================= */

@media(max-width:850px) {

    body {
        padding: 15px;
    }

    .container {

        grid-template-columns: 1fr;

        padding: 20px;

        gap: 30px;
    }

    .vinyl-area {
        order: 1;
    }

    .spotify {
        order: 2;
    }

    .turntable {

        width: min(
            380px,
            85vw
        );
    }

    #spotify-player {

        min-height: 600px;
    }
}

</style>
</head>

<body>

<div class="container">

    <!-- =========================
         SPOTIFY
    ========================= -->

    <section class="spotify">

        <div class="header">

            <h1>My Spotify</h1>

            <p>
                Put some music on.
            </p>

        </div>

        <!--
            Spotify va a crear el reproductor aquí.
        -->

        <div id="spotify-player"></div>

    </section>


    <!-- =========================
         VINILO
    ========================= -->

    <section class="vinyl-area">

        <div class="turntable">

            <div
                class="vinyl"
                id="vinyl"
            >

                <div class="label">

                    <span>
                        MY<br>
                        RECORD
                    </span>

                </div>

                <div class="hole"></div>

            </div>

            <div class="arm"></div>

        </div>


        <div
            class="status"
            id="status"
        >

            <div class="dot"></div>

            <span id="statusText">
                Paused
            </span>

        </div>

    </section>

</div>


<script>

/*
====================================================
SPOTIFY PLAYLIST
====================================================
*/

const playlistURL =
    "https://open.spotify.com/playlist/0aFukFImzZqlBhQzskT2T3";


/*
====================================================
ELEMENTOS
====================================================
*/

const vinyl =
    document.getElementById("vinyl");

const status =
    document.getElementById("status");

const statusText =
    document.getElementById("statusText");


/*
====================================================
CONTROL DEL VINILO
====================================================
*/

function startVinyl() {

    vinyl.classList.add("playing");

    status.classList.add("playing");

    statusText.textContent =
        "Playing";

}


function stopVinyl() {

    vinyl.classList.remove("playing");

    status.classList.remove("playing");

    statusText.textContent =
        "Paused";

}


/*
====================================================
SPOTIFY IFRAME API
====================================================

Spotify llama esta función cuando
la API está lista.
*/

window.onSpotifyIframeApiReady =
    (IFrameAPI) => {

        const element =
            document.getElementById(
                "spotify-player"
            );


        /*
        Configuración del Embed
        */

        const options = {

            width: "100%",

            height: "600",

            url: playlistURL

        };


        /*
        Crear reproductor
        */

        IFrameAPI.createController(

            element,

            options,

            (EmbedController) => {


                /*
                ====================================
                CUANDO COMIENZA UNA CANCIÓN
                ====================================
                */

                EmbedController.addListener(

                    "playback_started",

                    () => {

                        console.log(
                            "Spotify: PLAY"
                        );

                        startVinyl();

                    }

                );


                /*
                ====================================
                CUANDO CAMBIA PLAY/PAUSE
                ====================================
                */

                EmbedController.addListener(

                    "playback_update",

                    (event) => {

                        if (
                            !event ||
                            !event.data
                        ) {
                            return;
                        }


                        console.log(
                            "Spotify state:",
                            event.data
                        );


                        /*
                        isPaused = true
                        */

                        if (
                            event.data.isPaused
                        ) {

                            stopVinyl();

                        }

                        /*
                        isPaused = false
                        */

                        else {

                            startVinyl();

                        }

                    }

                );


                /*
                ====================================
                REPRODUCTOR LISTO
                ====================================
                */

                EmbedController.addListener(

                    "ready",

                    () => {

                        console.log(
                            "Spotify Embed listo."
                        );

                    }

                );

            }

        );

    };

</script>

</body>
</html>
