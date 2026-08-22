<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Spotify Vinyl</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    min-height: 100vh;
    background:
        radial-gradient(circle at 20% 20%, #252525, transparent 35%),
        radial-gradient(circle at 80% 80%, #151515, transparent 40%),
        #050505;

    color: white;
    font-family: Arial, Helvetica, sans-serif;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 25px;
}

/* ==============================
   CONTENEDOR
============================== */

.container {
    width: min(1200px, 100%);
    min-height: 680px;

    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 35px;

    padding: 30px;

    background: rgba(18,18,18,.92);

    border: 1px solid rgba(255,255,255,.08);

    border-radius: 25px;

    box-shadow:
        0 30px 80px rgba(0,0,0,.7),
        inset 0 0 40px rgba(255,255,255,.02);
}

/* ==============================
   SPOTIFY
============================== */

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

.spotify-window {
    width: 100%;
    height: 600px;

    border-radius: 18px;

    overflow: hidden;

    background: #121212;

    box-shadow:
        0 15px 40px rgba(0,0,0,.5);
}

.spotify-window iframe {
    width: 100%;
    height: 100%;

    border: none;
}

/* ==============================
   VINILO
============================== */

.vinyl-area {
    display: flex;
    flex-direction: column;

    align-items: center;
    justify-content: center;
}

.turntable {
    width: min(450px, 80vw);
    aspect-ratio: 1;

    border-radius: 28px;

    background:
        linear-gradient(
            145deg,
            #1b1b1b,
            #090909
        );

    display: flex;
    align-items: center;
    justify-content: center;

    position: relative;

    box-shadow:
        0 25px 60px rgba(0,0,0,.7),
        inset 0 0 40px rgba(0,0,0,.7);
}

/* ==============================
   VINYL DISC
============================== */

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
            #0a0a0a 6px
        );

    box-shadow:
        0 20px 35px rgba(0,0,0,.8),
        inset 0 0 25px rgba(255,255,255,.04);

    animation: spin 4s linear infinite;

    animation-play-state: paused;
}

/* Girar */

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

/* ==============================
   REFLEJOS
============================== */

.vinyl::before {

    content: "";

    position: absolute;

    inset: 0;

    border-radius: 50%;

    background:
        linear-gradient(
            135deg,
            rgba(255,255,255,.08),
            transparent 25%,
            transparent 70%,
            rgba(255,255,255,.04)
        );

    pointer-events: none;
}

/* ==============================
   LABEL
============================== */

.label {

    position: absolute;

    width: 32%;
    aspect-ratio: 1;

    left: 50%;
    top: 50%;

    transform: translate(-50%, -50%);

    border-radius: 50%;

    background:
        radial-gradient(
            circle,
            #555,
            #292929 55%,
            #111
        );

    border: 2px solid rgba(255,255,255,.12);

    display: flex;
    justify-content: center;
    align-items: center;

    text-align: center;

    box-shadow:
        inset 0 0 20px rgba(0,0,0,.6);
}

.label span {

    font-size: 11px;

    letter-spacing: 2px;

    font-weight: bold;

    color: #ddd;

}

/* Agujero */

.hole {

    position: absolute;

    width: 9px;
    height: 9px;

    background: #050505;

    border-radius: 50%;

    left: 50%;
    top: 50%;

    transform: translate(-50%, -50%);

    box-shadow:
        0 0 0 2px rgba(255,255,255,.1);
}

/* ==============================
   BRAZO DEL TOCADISCOS
============================== */

.arm {

    position: absolute;

    width: 42%;

    height: 8px;

    background: #777;

    border-radius: 10px;

    right: 3%;
    top: 16%;

    transform: rotate(25deg);

    transform-origin: right center;

    box-shadow:
        0 3px 8px rgba(0,0,0,.7);
}

.arm::after {

    content: "";

    position: absolute;

    right: -3px;
    top: -4px;

    width: 16px;
    height: 16px;

    border-radius: 50%;

    background: #aaa;
}

/* ==============================
   STATUS
============================== */

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

}

.status.playing {

    color: #1ed760;
}

.status.playing .dot {

    background: #1ed760;

    box-shadow:
        0 0 12px #1ed760;
}

/* ==============================
   MOBILE
============================== */

@media(max-width: 850px) {

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

        width: min(380px, 85vw);
    }

    .spotify-window {

        height: 600px;
    }

}
</style>
</head>

<body>

<div class="container">

    <!-- ==========================
         SPOTIFY
    =========================== -->

    <section class="spotify">

        <div class="header">

            <h1>My Spotify</h1>

            <p>
                Put some music on.
            </p>

        </div>

        <div class="spotify-window">

            <iframe
                src="https://open.spotify.com/embed/playlist/0aFukFImzZqlBhQzskT2T3?utm_source=generator&theme=0"
                allow="
                    autoplay;
                    clipboard-write;
                    encrypted-media;
                    fullscreen;
                    picture-in-picture
                "
                loading="lazy">
            </iframe>

        </div>

    </section>


    <!-- ==========================
         VINILO
    =========================== -->

    <section class="vinyl-area">

        <div class="turntable">

            <div class="vinyl" id="vinyl">

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


        <div class="status" id="status">

            <div class="dot"></div>

            <span id="statusText">
                Paused
            </span>

        </div>

    </section>

</div>


<script>

/*
========================================
VINYL CONTROL
========================================

El Embed de Spotify está aislado por
seguridad, así que el navegador no puede
leer directamente si Spotify está
reproduciendo.

El botón de Spotify puede activar el
vinilo manualmente mediante este pequeño
control.
========================================
*/

const vinyl = document.getElementById("vinyl");

const status = document.getElementById("status");

const statusText = document.getElementById("statusText");


function playVinyl() {

    vinyl.classList.add("playing");

    status.classList.add("playing");

    statusText.textContent = "Playing";

}


function pauseVinyl() {

    vinyl.classList.remove("playing");

    status.classList.remove("playing");

    statusText.textContent = "Paused";

}


/*
========================================
CLICK EN EL VINILO
========================================

Puedes usar el vinilo como interruptor
visual.
========================================
*/

vinyl.addEventListener("click", () => {

    if (vinyl.classList.contains("playing")) {

        pauseVinyl();

    } else {

        playVinyl();

    }

});


/*
========================================
ATAJO DE TECLADO

Espacio = play / pause del vinilo
========================================
*/

document.addEventListener("keydown", (event) => {

    if (event.code === "Space") {

        event.preventDefault();

        if (vinyl.classList.contains("playing")) {

            pauseVinyl();

        } else {

            playVinyl();

        }

    }

});

</script>

</body>
</html>
