<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Spotify Vinyl</title>

<style>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {

    min-height: 100vh;

    background:
        radial-gradient(
            circle at 20% 20%,
            #292929,
            transparent 35%
        ),
        radial-gradient(
            circle at 80% 80%,
            #171717,
            transparent 40%
        ),
        #050505;

    color: white;

    font-family:
        Arial,
        Helvetica,
        sans-serif;

    display: flex;

    justify-content: center;

    align-items: center;

    padding: 25px;

}


/* =====================================
   MAIN
===================================== */

.container {

    width: min(1200px, 100%);

    min-height: 680px;

    display: grid;

    grid-template-columns:
        1fr
        1fr;

    gap: 35px;

    padding: 30px;

    background:
        rgba(18,18,18,.94);

    border:
        1px solid
        rgba(255,255,255,.08);

    border-radius: 25px;

    box-shadow:
        0 30px 80px
        rgba(0,0,0,.75);

}


/* =====================================
   SPOTIFY
===================================== */

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

}


.header p {

    color: #888;

    margin-top: 6px;

    font-size: 14px;

}


.spotify-window {

    width: 100%;

    height: 600px;

    border-radius: 18px;

    overflow: hidden;

    background: #121212;

}


.spotify-window iframe {

    width: 100%;

    height: 100%;

    border: none;

}


/* =====================================
   VINYL AREA
===================================== */

.vinyl-area {

    display: flex;

    flex-direction: column;

    justify-content: center;

    align-items: center;

}


/* =====================================
   TURNTABLE
===================================== */

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
            #1c1c1c,
            #080808
        );

    box-shadow:
        0 25px 60px
        rgba(0,0,0,.75),

        inset 0 0 40px
        rgba(0,0,0,.8);

}


/* =====================================
   VINYL
===================================== */

.vinyl {

    width: 78%;

    aspect-ratio: 1;

    position: relative;

    border-radius: 50%;

    cursor: pointer;

    background:

        repeating-radial-gradient(
            circle,
            #030303 0px,
            #111 2px,
            #050505 4px,
            #0c0c0c 6px
        );

    box-shadow:

        0 20px 40px
        rgba(0,0,0,.85),

        inset 0 0 30px
        rgba(255,255,255,.05);

    /*
       IMPORTANTE:
       La animación siempre existe.
    */

    animation:
        vinylSpin
        3.5s
        linear
        infinite;

}


/* =====================================
   ANIMACIÓN
===================================== */

@keyframes vinylSpin {

    from {

        transform:
            rotate(0deg);

    }

    to {

        transform:
            rotate(360deg);

    }

}


/* =====================================
   PAUSAR VINILO
===================================== */

.vinyl.paused {

    animation-play-state:
        paused;

}


/* =====================================
   REFLEJO
===================================== */

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


/* =====================================
   LABEL
===================================== */

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
        2px solid
        rgba(255,255,255,.12);

    display: flex;

    justify-content: center;

    align-items: center;

    text-align: center;

}


.label span {

    font-size: 11px;

    font-weight: bold;

    letter-spacing: 2px;

    color: #ddd;

}


/* =====================================
   CENTRO
===================================== */

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

}


/* =====================================
   BRAZO
===================================== */

.arm {

    position: absolute;

    width: 42%;

    height: 8px;

    right: 3%;

    top: 16%;

    background: #777;

    border-radius: 10px;

    transform:
        rotate(25deg);

    box-shadow:
        0 4px 10px
        rgba(0,0,0,.7);

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


/* =====================================
   STATUS
===================================== */

.status {

    margin-top: 25px;

    display: flex;

    align-items: center;

    gap: 10px;

    color: #1ed760;

    font-size: 13px;

    letter-spacing: 1px;

    text-transform: uppercase;

}


.dot {

    width: 9px;

    height: 9px;

    border-radius: 50%;

    background: #1ed760;

    box-shadow:
        0 0 12px
        #1ed760;

}


/* =====================================
   MOBILE
===================================== */

@media(max-width:850px) {

    body {

        padding: 15px;

    }


    .container {

        grid-template-columns: 1fr;

        padding: 20px;

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

}

</style>

</head>


<body>


<div class="container">


    <!-- ==============================
         SPOTIFY
    =============================== -->

    <section class="spotify">

        <div class="header">

            <h1>
                My Spotify
            </h1>

            <p>
                Put some music on.
            </p>

        </div>


        <div class="spotify-window">

            <iframe

                src="
                https://open.spotify.com/embed/playlist/0aFukFImzZqlBhQzskT2T3?utm_source=generator&theme=0
                "

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


    <!-- ==============================
         VINILO
    =============================== -->

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


        <div class="status">

            <div class="dot"></div>

            <span id="statusText">

                Playing

            </span>

        </div>


    </section>


</div>


<script>


const vinyl =
    document.getElementById(
        "vinyl"
    );


const statusText =
    document.getElementById(
        "statusText"
    );


/*
=========================================
ESTADO INICIAL

El vinilo comienza girando.
=========================================
*/

let playing = true;


/*
=========================================
CLICK EN VINILO
=========================================
*/

vinyl.addEventListener(
    "click",
    () => {

        playing = !playing;


        if (playing) {

            vinyl.classList.remove(
                "paused"
            );

            statusText.textContent =
                "Playing";

        }

        else {

            vinyl.classList.add(
                "paused"
            );

            statusText.textContent =
                "Paused";

        }

    }
);


/*
=========================================
TECLA ESPACIO
=========================================
*/

document.addEventListener(
    "keydown",
    (event) => {

        if (
            event.code ===
            "Space"
        ) {

            event.preventDefault();

            vinyl.click();

        }

    }
);


</script>


</body>

</html>
