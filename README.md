<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Media Room</title>

<script src="https://open.spotify.com/embed/iframe-api/v1" async></script>

<style>

/* =====================================================
   RESET
===================================================== */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    min-height: 100vh;

    background: #050505;

    color: white;

    font-family:
        Arial,
        Helvetica,
        sans-serif;

    overflow-x: hidden;
}


/* =====================================================
   BOOT SCREEN
===================================================== */

#boot-screen {

    position: fixed;

    inset: 0;

    z-index: 99999;

    background: #050505;

    color: #d7d7d7;

    font-family:
        "Courier New",
        monospace;

    display: flex;

    flex-direction: column;

    padding: 30px;

    overflow: hidden;

    transition:
        opacity .8s ease,
        visibility .8s ease;

}


/* =====================================================
   BOOT TOP
===================================================== */

.boot-top {

    display: flex;

    justify-content: space-between;

    align-items: center;

    border-bottom:
        1px solid #333;

    padding-bottom: 12px;

    margin-bottom: 20px;

    font-size: 13px;

}


.boot-logo {

    font-size: 18px;

    font-weight: bold;

    letter-spacing: 2px;

}


/* =====================================================
   CODE AREA
===================================================== */

#boot-code {

    flex: 1;

    overflow: hidden;

    font-size: 12px;

    line-height: 1.55;

    color: #a9a9a9;

    opacity: .9;

}


/* diferentes líneas */

.code-line {
    white-space: nowrap;
}

.code-green {
    color: #79ff79;
}

.code-white {
    color: #ddd;
}

.code-gray {
    color: #666;
}

.code-blue {
    color: #8bbcff;
}


/* =====================================================
   BOOT BOTTOM
===================================================== */

.boot-bottom {

    border-top:
        1px solid #333;

    padding-top: 18px;

    margin-top: 15px;

}


/* =====================================================
   PROGRESS
===================================================== */

.progress-container {

    width: 100%;

    height: 14px;

    border:
        1px solid #555;

    margin-top: 12px;

    padding: 2px;

}


#progress {

    width: 0%;

    height: 100%;

    background: #ddd;

    transition:
        width .1s linear;

}


/* =====================================================
   STATUS
===================================================== */

#boot-status {

    margin-top: 12px;

    font-size: 13px;

}


/* =====================================================
   CURSOR
===================================================== */

.cursor {

    display: inline-block;

    width: 8px;

    height: 14px;

    background: #ddd;

    animation:
        blink .8s infinite;

    vertical-align: middle;

}

@keyframes blink {

    0%, 50% {
        opacity: 1;
    }

    51%, 100% {
        opacity: 0;
    }

}


/* =====================================================
   READY SCREEN
===================================================== */

#ready {

    position: absolute;

    inset: 0;

    background: #050505;

    display: flex;

    align-items: center;

    justify-content: center;

    flex-direction: column;

    opacity: 0;

    pointer-events: none;

    transition:
        opacity .5s ease;

}


#ready h1 {

    font-size: 25px;

    letter-spacing: 5px;

}


#ready p {

    margin-top: 12px;

    color: #777;

    font-size: 12px;

}


/* =====================================================
   NAVBAR
===================================================== */

.navbar {

    position: sticky;

    top: 0;

    z-index: 1000;

    width: 100%;

    padding:
        18px 30px;

    background:
        rgba(5,5,5,.85);

    backdrop-filter:
        blur(18px);

    border-bottom:
        1px solid
        rgba(255,255,255,.08);

    display: flex;

    align-items: center;

    justify-content: space-between;

}


.logo {

    font-size: 20px;

    font-weight: bold;

    letter-spacing: 2px;

}


.nav-buttons {

    display: flex;

    gap: 8px;

}


.nav-btn {

    border: none;

    color: #aaa;

    background: transparent;

    padding:
        10px 15px;

    border-radius: 10px;

    cursor: pointer;

    font-size: 13px;

    transition: .25s;

}


.nav-btn:hover {

    background: #1b1b1b;

    color: white;

}


.nav-btn.active {

    background: white;

    color: #050505;

}


/* =====================================================
   MAIN
===================================================== */

main {

    width:
        min(1250px, 94%);

    margin: auto;

}


.section {

    display: none;

    min-height:
        calc(100vh - 75px);

    padding:
        50px 0;

}


.section.active {

    display: block;

}


.section-header {

    margin-bottom: 30px;

}


.section-header h1 {

    font-size:
        clamp(30px, 5vw, 52px);

    letter-spacing: -2px;

}


.section-header p {

    color: #888;

    margin-top: 8px;

    font-size: 14px;

}


/* =====================================================
   SPOTIFY
===================================================== */

.spotify-layout {

    display: grid;

    grid-template-columns:
        1fr 1fr;

    gap: 35px;

    align-items: center;

}


.spotify-window {

    width: 100%;

    height: 600px;

    border-radius: 20px;

    overflow: hidden;

    background: #121212;

    box-shadow:
        0 25px 60px
        rgba(0,0,0,.65);

}


#spotify-player {

    width: 100%;

    height: 100%;

}


/* =====================================================
   TURNTABLE
===================================================== */

.turntable {

    width:
        min(480px, 90vw);

    aspect-ratio: 1;

    margin: auto;

    position: relative;

    display: flex;

    align-items: center;

    justify-content: center;

    border-radius: 30px;

    background:
        linear-gradient(
            145deg,
            #202020,
            #080808
        );

    box-shadow:
        0 30px 70px
        rgba(0,0,0,.8),

        inset 0 0 40px
        rgba(0,0,0,.8);

}


/* =====================================================
   VINYL
===================================================== */

.vinyl {

    width: 76%;

    aspect-ratio: 1;

    border-radius: 50%;

    position: relative;

    background:
        repeating-radial-gradient(
            circle,
            #020202 0px,
            #101010 2px,
            #040404 4px,
            #0b0b0b 6px
        );

    box-shadow:
        0 20px 40px
        rgba(0,0,0,.9),

        inset 0 0 30px
        rgba(255,255,255,.04);

    animation:
        vinylSpin
        4s
        linear
        infinite;

    animation-play-state:
        paused;

}


.vinyl.playing {

    animation-play-state:
        running;

}


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


.vinyl::before {

    content: "";

    position: absolute;

    inset: 0;

    border-radius: 50%;

    background:
        linear-gradient(
            135deg,
            rgba(255,255,255,.11),
            transparent 25%,
            transparent 70%,
            rgba(255,255,255,.03)
        );

}


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
            #282828 55%,
            #111
        );

    display: flex;

    align-items: center;

    justify-content: center;

    text-align: center;

    border:
        2px solid
        rgba(255,255,255,.12);

}


.label span {

    font-size: 10px;

    font-weight: bold;

    letter-spacing: 2px;

}


.hole {

    position: absolute;

    width: 9px;

    height: 9px;

    left: 50%;
    top: 50%;

    transform:
        translate(-50%, -50%);

    border-radius: 50%;

    background: #000;

}


.arm {

    position: absolute;

    width: 42%;

    height: 8px;

    right: 3%;

    top: 15%;

    border-radius: 10px;

    background: #777;

    transform:
        rotate(25deg);

    transform-origin:
        right center;

}


.arm::after {

    content: "";

    position: absolute;

    right: -5px;

    top: -4px;

    width: 16px;

    height: 16px;

    border-radius: 50%;

    background: #aaa;

}


/* =====================================================
   STATUS
===================================================== */

.status {

    display: flex;

    justify-content: center;

    align-items: center;

    gap: 10px;

    margin-top: 22px;

    color: #777;

    font-size: 12px;

    text-transform: uppercase;

    letter-spacing: 2px;

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
        0 0 12px
        #1ed760;

}


/* =====================================================
   ART
===================================================== */

.art-gallery {

    display: grid;

    grid-template-columns:
        repeat(
            auto-fit,
            minmax(230px, 1fr)
        );

    gap: 25px;

}


.art-card {

    background: #111;

    border:
        1px solid
        rgba(255,255,255,.08);

    border-radius: 18px;

    overflow: hidden;

    transition:
        transform .3s,
        box-shadow .3s;

}


.art-card:hover {

    transform:
        translateY(-8px);

    box-shadow:
        0 20px 50px
        rgba(0,0,0,.6);

}


.art-image {

    width: 100%;

    aspect-ratio: 4 / 5;

    background:
        linear-gradient(
            135deg,
            #272727,
            #090909
        );

    display: flex;

    align-items: center;

    justify-content: center;

    overflow: hidden;

}


.art-image img {

    width: 100%;

    height: 100%;

    object-fit: cover;

}


.art-placeholder {

    color: #555;

    font-size: 50px;

}


.art-info {

    padding: 18px;

}


.art-info h2 {

    font-size: 17px;

}


.art-info p {

    color: #777;

    margin-top: 6px;

    font-size: 13px;

}


/* =====================================================
   BOOKS
===================================================== */

.book-grid {

    display: grid;

    grid-template-columns:
        repeat(
            auto-fit,
            minmax(210px, 1fr)
        );

    gap: 25px;

}


.book {

    background: #111;

    border:
        1px solid
        rgba(255,255,255,.08);

    border-radius: 18px;

    padding: 15px;

    transition:
        transform .3s,
        box-shadow .3s;

}


.book:hover {

    transform:
        translateY(-8px);

    box-shadow:
        0 20px 50px
        rgba(0,0,0,.6);

}


.book-cover {

    width: 100%;

    aspect-ratio: 2 / 3;

    border-radius: 10px;

    background:
        linear-gradient(
            145deg,
            #292929,
            #0b0b0b
        );

    display: flex;

    justify-content: center;

    align-items: center;

    text-align: center;

    padding: 20px;

    color: #777;

    font-size: 40px;

    overflow: hidden;

}


.book-cover img {

    width: 100%;

    height: 100%;

    object-fit: cover;

}


.book-info {

    padding-top: 15px;

}


.book-info h2 {

    font-size: 17px;

}


.book-info p {

    margin-top: 6px;

    color: #777;

    font-size: 13px;

}


.book-button {

    display: block;

    width: 100%;

    margin-top: 15px;

    padding: 10px;

    border: none;

    border-radius: 9px;

    background: #222;

    color: white;

    text-decoration: none;

    text-align: center;

    font-size: 12px;

}


.book-button:hover {

    background: white;

    color: black;

}


/* =====================================================
   MOBILE
===================================================== */

@media(max-width:850px) {

    .navbar {

        padding: 15px;

        flex-direction: column;

        gap: 12px;

    }

    .nav-buttons {

        width: 100%;

        justify-content: center;

    }

    .nav-btn {

        flex: 1;

        padding:
            9px 6px;

    }

    .spotify-layout {

        grid-template-columns: 1fr;

    }

    .spotify-window {

        height: 600px;

    }

}

</style>
</head>


<body>


<!-- =====================================================
     BOOT SCREEN
===================================================== -->

<div id="boot-screen">


    <div class="boot-top">

        <div class="boot-logo">
            MEDIA ROOM COMPUTER
        </div>

        <div>
            BIOS 1.94
        </div>

    </div>


    <div id="boot-code"></div>


    <div class="boot-bottom">

        <div id="boot-status">
            Initializing system...
        </div>

        <div class="progress-container">

            <div id="progress"></div>

        </div>

        <div style="margin-top:12px;">
            C:\MEDIA_ROOM&gt; <span class="cursor"></span>
        </div>

    </div>


    <div id="ready">

        <h1>
            SYSTEM READY
        </h1>

        <p>
            Welcome to MEDIA ROOM
        </p>

    </div>

</div>


<!-- =====================================================
     NAVIGATION
===================================================== -->

<nav class="navbar">

    <div class="logo">
        MEDIA ROOM
    </div>


    <div class="nav-buttons">

        <button
            class="nav-btn active"
            onclick="showSection('music', this)"
        >
            🎵 Música
        </button>

        <button
            class="nav-btn"
            onclick="showSection('art', this)"
        >
            🎨 Arte
        </button>

        <button
            class="nav-btn"
            onclick="showSection('books', this)"
        >
            📚 Libros
        </button>

    </div>

</nav>


<main>


<!-- =====================================================
     MUSIC
===================================================== -->

<section
    id="music"
    class="section active"
>

    <div class="section-header">

        <h1>
            Music
        </h1>

        <p>
            Spotify & vinyl player.
        </p>

    </div>


    <div class="spotify-layout">


        <div class="spotify-window">

            <div
                id="spotify-player">
            </div>

        </div>


        <div>

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

        </div>

    </div>

</section>


<!-- =====================================================
     ART
===================================================== -->

<section
    id="art"
    class="section"
>

    <div class="section-header">

        <h1>
            Art
        </h1>

        <p>
            A small personal gallery.
        </p>

    </div>


    <div class="art-gallery">


        <article class="art-card">

            <div class="art-image">

                <div class="art-placeholder">
                    🎨
                </div>

            </div>

            <div class="art-info">

                <h2>
                    Painting I
                </h2>

                <p>
                    Add your artwork here.
                </p>

            </div>

        </article>


        <article class="art-card">

            <div class="art-image">

                <div class="art-placeholder">
                    🖼️
                </div>

            </div>

            <div class="art-info">

                <h2>
                    Painting II
                </h2>

                <p>
                    Another piece of art.
                </p>

            </div>

        </article>


        <article class="art-card">

            <div class="art-image">

                <div class="art-placeholder">
                    🖌️
                </div>

            </div>

            <div class="art-info">

                <h2>
                    Painting III
                </h2>

                <p>
                    Your description here.
                </p>

            </div>

        </article>


        <article class="art-card">

            <div class="art-image">

                <div class="art-placeholder">
                    ✏️
                </div>

            </div>

            <div class="art-info">

                <h2>
                    Drawing
                </h2>

                <p>
                    Add another artwork.
                </p>

            </div>

        </article>


    </div>

</section>


<!-- =====================================================
     BOOKS
===================================================== -->

<section
    id="books"
    class="section"
>

    <div class="section-header">

        <h1>
            Library
        </h1>

        <p>
            Books, stories and things worth reading.
        </p>

    </div>


    <div class="book-grid">


        <article class="book">

            <div class="book-cover">
                📖
            </div>

            <div class="book-info">

                <h2>
                    Book One
                </h2>

                <p>
                    Author name
                </p>

                <a
                    href="#"
                    class="book-button"
                >
                    Open book
                </a>

            </div>

        </article>


        <article class="book">

            <div class="book-cover">
                📕
            </div>

            <div class="book-info">

                <h2>
                    Book Two
                </h2>

                <p>
                    Author name
                </p>

                <a
                    href="#"
                    class="book-button"
                >
                    Open book
                </a>

            </div>

        </article>


        <article class="book">

            <div class="book-cover">
                📗
            </div>

            <div class="book-info">

                <h2>
                    Book Three
                </h2>

                <p>
                    Author name
                </p>

                <a
                    href="#"
                    class="book-button"
                >
                    Open book
                </a>

            </div>

        </article>


        <article class="book">

            <div class="book-cover">
                📘
            </div>

            <div class="book-info">

                <h2>
                    Book Four
                </h2>

                <p>
                    Author name
                </p>

                <a
                    href="#"
                    class="book-button"
                >
                    Open book
                </a>

            </div>

        </article>


    </div>

</section>


</main>


<script>

/* =====================================================
   RETRO BOOT SEQUENCE
===================================================== */

const bootCode =
    document.getElementById(
        "boot-code"
    );

const progress =
    document.getElementById(
        "progress"
    );

const bootStatus =
    document.getElementById(
        "boot-status"
    );

const bootScreen =
    document.getElementById(
        "boot-screen"
    );

const ready =
    document.getElementById(
        "ready"
    );


/* código falso estilo terminal */

const codeFragments = [

    "0x0000A4F2  SYSTEM_INIT",
    "0x0000B81C  MEMORY CHECK ........ OK",
    "0x0000C920  CPU INITIALIZATION",
    "0x0000D118  GRAPHICS DRIVER ..... OK",
    "0x0000E004  AUDIO DRIVER ........ OK",
    "0x0000EFA2  MEDIA ENGINE ........ OK",
    "0x0001A882  LOADING KERNEL",
    "0x0001B901  CHECKING FILE SYSTEM",
    "0x0001C442  MOUNTING /MEDIA",
    "0x0001D781  SCANNING DEVICES",
    "0x0001E902  DEVICE 00 ............ READY",
    "0x00020A11  DEVICE 01 ............ READY",
    "0x00021D90  CACHE ................. READY",
    "0x00022FA1  NETWORK ............... READY",
    "0x000231B8  USER INTERFACE ........ OK",
    "0x00024AA1  LOADING SPOTIFY MODULE",
    "0x00025BC2  LOADING ART MODULE",
    "0x00026DA8  LOADING LIBRARY MODULE",
    "0x00028A10  INDEXING MEDIA",
    "0x00029C77  BUILDING DATABASE",
    "0x0002AE18  CHECKING PERMISSIONS",
    "0x0002B991  STARTING MEDIA ROOM",
    "0x0002C812  SYSTEM CHECK .......... OK",
    "0x0002D551  ALL SYSTEMS NOMINAL"

];


/* generar líneas */

function addCodeLine() {

    const line =
        document.createElement(
            "div"
        );

    const random =
        codeFragments[
            Math.floor(
                Math.random()
                *
                codeFragments.length
            )
        ];


    const hex =
        Math.floor(
            Math.random()
            *
            0xFFFFFF
        )
        .toString(16)
        .toUpperCase();


    line.className =
        "code-line";


    line.innerHTML =
        `<span class="code-gray">
            0x${hex}
        </span>
        &nbsp;
        <span class="code-white">
            ${random}
        </span>`;


    bootCode.appendChild(
        line
    );


    /*
       Mantener solo las últimas
       líneas para que no explote
       el navegador.
    */

    if (
        bootCode.children.length
        > 42
    ) {

        bootCode.removeChild(
            bootCode.firstChild
        );

    }


    bootCode.scrollTop =
        bootCode.scrollHeight;

}


/* llenar código */

let codeInterval =
    setInterval(
        addCodeLine,
        45
    );


/* =====================================================
   PROGRESO
===================================================== */

let percent = 0;


const progressInterval =
    setInterval(
        () => {

            percent +=
                Math.random() * 3;

            if (
                percent >= 100
            ) {

                percent = 100;

                clearInterval(
                    progressInterval
                );

                clearInterval(
                    codeInterval
                );


                bootStatus.textContent =
                    "SYSTEM READY";


                /*
                   Mostrar READY
                */

                setTimeout(
                    () => {

                        ready.style.opacity =
                            "1";

                    },
                    200
                );


                /*
                   Salir del boot
                */

                setTimeout(
                    () => {

                        bootScreen.style.opacity =
                            "0";

                        bootScreen.style.visibility =
                            "hidden";

                        document.body.style.overflowX =
                            "hidden";

                    },
                    1400
                );

            }


            progress.style.width =
                percent + "%";


            /*
               Cambiar mensajes
               según progreso
            */

            if (percent < 20) {

                bootStatus.textContent =
                    "Initializing hardware...";

            }

            else if (percent < 40) {

                bootStatus.textContent =
                    "Loading system drivers...";

            }

            else if (percent < 60) {

                bootStatus.textContent =
                    "Mounting media devices...";

            }

            else if (percent < 80) {

                bootStatus.textContent =
                    "Loading Media Room...";

            }

            else {

                bootStatus.textContent =
                    "Finalizing startup...";

            }

        },

        100
    );


/* =====================================================
   NAVIGATION
===================================================== */

function showSection(
    sectionID,
    button
) {

    const sections =
        document.querySelectorAll(
            ".section"
        );

    const buttons =
        document.querySelectorAll(
            ".nav-btn"
        );


    sections.forEach(
        section => {

            section.classList.remove(
                "active"
            );

        }
    );


    buttons.forEach(
        btn => {

            btn.classList.remove(
                "active"
            );

        }
    );


    document
        .getElementById(
            sectionID
        )
        .classList.add(
            "active"
        );


    button.classList.add(
        "active"
    );

}


/* =====================================================
   SPOTIFY
===================================================== */

const playlistURL =
    "https://open.spotify.com/playlist/0aFukFImzZqlBhQzskT2T3";


const vinyl =
    document.getElementById(
        "vinyl"
    );

const status =
    document.getElementById(
        "status"
    );

const statusText =
    document.getElementById(
        "statusText"
    );


function startVinyl() {

    vinyl.classList.add(
        "playing"
    );

    status.classList.add(
        "playing"
    );

    statusText.textContent =
        "Playing";

}


function stopVinyl() {

    vinyl.classList.remove(
        "playing"
    );

    status.classList.remove(
        "playing"
    );

    statusText.textContent =
        "Paused";

}


/* =====================================================
   SPOTIFY IFRAME API
===================================================== */

window.onSpotifyIframeApiReady =
    (IFrameAPI) => {

        const element =
            document.getElementById(
                "spotify-player"
            );


        const options = {

            width: "100%",

            height: "600",

            url: playlistURL

        };


        IFrameAPI.createController(

            element,

            options,

            (EmbedController) => {


                EmbedController.addListener(

                    "playback_started",

                    () => {

                        startVinyl();

                    }

                );


                EmbedController.addListener(

                    "playback_update",

                    (event) => {

                        if (
                            !event ||
                            !event.data
                        ) {

                            return;

                        }


                        if (
                            event.data.isPaused
                        ) {

                            stopVinyl();

                        }

                        else {

                            startVinyl();

                        }

                    }

                );

            }

        );

    };

</script>

</body>
</html>
