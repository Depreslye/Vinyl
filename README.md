<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>MEDIA ROOM</title>

<script src="https://open.spotify.com/embed/iframe-api/v1" async></script>

<style>

/* =====================================================
   GLOBAL
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
    background: #050505;
    color: white;
    font-family: Arial, Helvetica, sans-serif;
    overflow-x: hidden;
}


/* =====================================================
   90s COMPUTER BOOT
===================================================== */

#boot-screen {
    position: fixed;
    inset: 0;
    z-index: 99999;

    background: #050505;
    color: #ccc;

    font-family: "Courier New", monospace;

    padding: 25px;

    display: flex;
    flex-direction: column;

    transition:
        opacity .8s ease,
        visibility .8s ease;
}

.boot-top {
    display: flex;
    justify-content: space-between;

    border-bottom: 1px solid #333;

    padding-bottom: 12px;
    margin-bottom: 15px;

    font-size: 12px;
}

.boot-logo {
    font-size: 17px;
    font-weight: bold;
    letter-spacing: 2px;
}

#boot-code {
    flex: 1;
    overflow: hidden;

    font-size: 11px;
    line-height: 1.5;
}

.code-line {
    white-space: nowrap;
}

.code-gray {
    color: #555;
}

.code-white {
    color: #bbb;
}

.code-green {
    color: #79ff79;
}

.code-blue {
    color: #8baeff;
}

.boot-bottom {
    border-top: 1px solid #333;

    padding-top: 15px;
}

#boot-status {
    font-size: 12px;
}

.progress-container {
    width: 100%;
    height: 13px;

    border: 1px solid #555;

    margin-top: 10px;

    padding: 2px;
}

#progress {
    height: 100%;
    width: 0%;

    background: #ddd;

    transition: width .1s linear;
}

.cursor {
    display: inline-block;

    width: 8px;
    height: 14px;

    background: white;

    animation: blink .8s infinite;
}

@keyframes blink {

    0%, 50% {
        opacity: 1;
    }

    51%, 100% {
        opacity: 0;
    }

}

#ready {
    position: absolute;
    inset: 0;

    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    background: #050505;

    opacity: 0;

    pointer-events: none;

    transition: opacity .5s;
}

#ready h1 {
    letter-spacing: 5px;
    font-size: 25px;
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

    padding: 18px 30px;

    background: rgba(5,5,5,.88);

    backdrop-filter: blur(18px);

    border-bottom: 1px solid #181818;

    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    font-size: 20px;
    font-weight: bold;
    letter-spacing: 2px;
}

.nav-buttons {
    display: flex;
    gap: 7px;
}

.nav-btn {
    background: transparent;

    border: none;

    color: #777;

    padding: 10px 14px;

    border-radius: 9px;

    cursor: pointer;

    transition: .2s;
}

.nav-btn:hover {
    background: #171717;
    color: white;
}

.nav-btn.active {
    background: white;
    color: black;
}


/* =====================================================
   SECTIONS
===================================================== */

main {
    width: min(1250px, 94%);
    margin: auto;
}

.section {
    display: none;

    min-height: calc(100vh - 75px);

    padding: 55px 0;
}

.section.active {
    display: block;
}

.section-header {
    margin-bottom: 35px;
}

.section-header h1 {
    font-size: clamp(32px, 5vw, 55px);
    letter-spacing: -2px;
}

.section-header p {
    margin-top: 8px;
    color: #777;
    font-size: 14px;
}


/* =====================================================
   SPOTIFY
===================================================== */

.spotify-layout {
    display: grid;

    grid-template-columns: 1fr 1fr;

    gap: 35px;

    align-items: center;
}

.spotify-window {
    width: 100%;
    height: 600px;

    background: #121212;

    border-radius: 20px;

    overflow: hidden;

    box-shadow:
        0 30px 70px rgba(0,0,0,.7);
}

#spotify-player {
    width: 100%;
    height: 100%;
}


/* =====================================================
   VINYL
===================================================== */

.turntable {
    width: min(480px, 90vw);

    aspect-ratio: 1;

    margin: auto;

    display: flex;

    justify-content: center;
    align-items: center;

    position: relative;

    border-radius: 30px;

    background:
        linear-gradient(
            145deg,
            #202020,
            #080808
        );

    box-shadow:
        0 30px 70px rgba(0,0,0,.8),
        inset 0 0 40px rgba(0,0,0,.8);
}

.vinyl {
    width: 76%;
    aspect-ratio: 1;

    position: relative;

    border-radius: 50%;

    background:
        repeating-radial-gradient(
            circle,
            #020202 0px,
            #101010 2px,
            #040404 4px,
            #0b0b0b 6px
        );

    box-shadow:
        0 20px 40px rgba(0,0,0,.9);

    animation:
        vinylSpin 4s linear infinite;

    animation-play-state: paused;
}

.vinyl.playing {
    animation-play-state: running;
}

@keyframes vinylSpin {

    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(360deg);
    }

}

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
            #777,
            #292929 55%,
            #111
        );

    display: flex;

    justify-content: center;
    align-items: center;

    text-align: center;
}

.label span {
    font-size: 9px;
    letter-spacing: 2px;
    font-weight: bold;
}

.hole {
    position: absolute;

    width: 9px;
    height: 9px;

    left: 50%;
    top: 50%;

    transform: translate(-50%, -50%);

    border-radius: 50%;

    background: black;
}

.arm {
    position: absolute;

    width: 42%;
    height: 8px;

    right: 3%;
    top: 15%;

    border-radius: 10px;

    background: #777;

    transform: rotate(25deg);

    transform-origin: right center;
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

.status {
    display: flex;

    justify-content: center;
    align-items: center;

    gap: 10px;

    margin-top: 20px;

    color: #777;

    font-family: monospace;

    font-size: 12px;

    letter-spacing: 2px;
}

.status.playing {
    color: #1ed760;
}

.dot {
    width: 9px;
    height: 9px;

    border-radius: 50%;

    background: #555;
}

.status.playing .dot {
    background: #1ed760;

    box-shadow:
        0 0 12px #1ed760;
}


/* =====================================================
   ART
===================================================== */

.art-gallery {
    display: grid;

    grid-template-columns:
        repeat(
            auto-fit,
            minmax(230px,1fr)
        );

    gap: 25px;
}

.art-card {
    background: #111;

    border: 1px solid #222;

    border-radius: 18px;

    overflow: hidden;

    transition: .3s;
}

.art-card:hover {
    transform: translateY(-8px);

    box-shadow:
        0 20px 50px rgba(0,0,0,.6);
}

.art-image {
    aspect-ratio: 4/5;

    display: flex;

    align-items: center;
    justify-content: center;

    background:
        linear-gradient(
            135deg,
            #292929,
            #080808
        );

    font-size: 55px;

    color: #555;
}

.art-info {
    padding: 18px;
}

.art-info h2 {
    font-size: 17px;
}

.art-info p {
    margin-top: 6px;

    color: #777;

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
            minmax(210px,1fr)
        );

    gap: 25px;
}

.book {
    background: #111;

    border: 1px solid #222;

    border-radius: 18px;

    padding: 15px;

    transition: .3s;
}

.book:hover {
    transform: translateY(-8px);

    box-shadow:
        0 20px 50px rgba(0,0,0,.6);
}

.book-cover {
    width: 100%;

    aspect-ratio: 2/3;

    border-radius: 10px;

    display: flex;

    align-items: center;
    justify-content: center;

    background:
        linear-gradient(
            145deg,
            #292929,
            #090909
        );

    font-size: 45px;

    color: #555;
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

    margin-top: 15px;

    padding: 10px;

    text-align: center;

    text-decoration: none;

    background: #222;

    color: white;

    border-radius: 9px;

    font-size: 12px;
}


/* =====================================================
   SECRET TERMINAL
===================================================== */

.code-terminal {
    width: 100%;

    max-width: 850px;

    margin: 50px auto;

    background: #030303;

    border: 1px solid #292929;

    border-radius: 12px;

    overflow: hidden;

    box-shadow:
        0 30px 80px rgba(0,0,0,.8);
}

.terminal-header {
    height: 42px;

    padding: 0 18px;

    display: flex;

    justify-content: space-between;

    align-items: center;

    background: #151515;

    border-bottom: 1px solid #292929;

    color: #777;

    font-family: monospace;

    font-size: 11px;

    letter-spacing: 1px;
}

.terminal-body {
    min-height: 440px;

    padding: 30px;

    font-family: "Courier New", monospace;

    background:
        radial-gradient(
            circle at center,
            #101010,
            #020202
        );

    position: relative;
}

.terminal-line {
    color: #666;

    line-height: 1.8;
}

#terminalTyping {
    color: #aaa;

    min-height: 25px;
}

.input-line {
    display: flex;

    align-items: center;

    gap: 10px;

    margin-top: 15px;

    color: #ddd;
}

.input-line input {
    flex: 1;

    background: transparent;

    border: none;

    outline: none;

    color: white;

    font-family: monospace;

    font-size: 16px;

    letter-spacing: 3px;
}

.input-line input::placeholder {
    color: #333;
}

.access-button {
    margin-top: 25px;

    padding: 11px 20px;

    background: #111;

    color: #aaa;

    border: 1px solid #333;

    border-radius: 6px;

    font-family: monospace;

    font-size: 11px;

    cursor: pointer;

    transition: .2s;
}

.access-button:hover {
    background: white;

    color: black;
}

.code-message {
    min-height: 25px;

    margin-top: 25px;

    font-size: 11px;

    letter-spacing: 1px;
}

.code-message.error {
    color: #c56b6b;
}

.code-message.success {
    color: #79ff79;

    text-shadow:
        0 0 8px rgba(121,255,121,.4);
}

.secret-result {
    display: none;

    margin-top: 25px;

    padding: 30px;

    border: 1px solid #333;

    background:
        linear-gradient(
            135deg,
            #111,
            #060606
        );

    color: #ddd;

    font-family: Georgia, serif;

    font-size: 21px;

    line-height: 1.6;

    font-style: italic;

    position: relative;

    overflow: hidden;
}

.secret-result.visible {
    display: block;

    animation:
        revealSecret .8s ease;
}

@keyframes revealSecret {

    0% {
        opacity: 0;
        transform: translateY(15px);
        filter: blur(8px);
    }

    100% {
        opacity: 1;
        transform: translateY(0);
        filter: blur(0);
    }

}

.scanline {
    position: absolute;

    left: 0;
    right: 0;

    height: 2px;

    background: rgba(255,255,255,.15);

    animation:
        scan 1.5s linear infinite;
}

@keyframes scan {

    from {
        top: 0;
    }

    to {
        top: 100%;
    }

}


/* =====================================================
   MOBILE
===================================================== */

@media(max-width:850px) {

    .navbar {
        flex-direction: column;

        gap: 12px;

        padding: 15px;
    }

    .nav-buttons {
        width: 100%;
    }

    .nav-btn {
        flex: 1;
        padding: 9px 5px;
    }

    .spotify-layout {
        grid-template-columns: 1fr;
    }

    .spotify-window {
        height: 600px;
    }

    #boot-screen {
        padding: 15px;
    }

    #boot-code {
        font-size: 9px;
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
            C:\MEDIA_ROOM&gt;
            <span class="cursor"></span>
        </div>

    </div>


    <div id="ready">

        <h1>
            SYSTEM READY
        </h1>

        <p>
            USER RECOGNIZED
        </p>

        <p style="margin-top:8px;">
            WELCOME BACK
        </p>

    </div>

</div>


<!-- =====================================================
     NAVBAR
===================================================== -->

<nav class="navbar">

    <div class="logo">
        MEDIA ROOM
    </div>


    <div class="nav-buttons">

        <button
            class="nav-btn active"
            onclick="showSection('music',this)"
        >
            🎵 Music
        </button>

        <button
            class="nav-btn"
            onclick="showSection('art',this)"
        >
            🎨 Art
        </button>

        <button
            class="nav-btn"
            onclick="showSection('books',this)"
        >
            📚 Books
        </button>

        <button
            class="nav-btn"
            onclick="showSection('codes',this)"
        >
            🔐 Codes
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

        <h1>Music</h1>

        <p>
            Spotify & vinyl player.
        </p>

    </div>


    <div class="spotify-layout">


        <div class="spotify-window">

            <div id="spotify-player"></div>

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
                    PAUSED
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

        <h1>Art</h1>

        <p>
            A small personal gallery.
        </p>

    </div>


    <div class="art-gallery">

        <article class="art-card">

            <div class="art-image">
                🎨
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
                🖼️
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
                🖌️
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
                ✏️
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

        <h1>Library</h1>

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


<!-- =====================================================
     SECRET CODES
===================================================== -->

<section
    id="codes"
    class="section"
>

    <div class="section-header">

        <h1>
            Restricted Archive
        </h1>

        <p>
            Enter an access code to retrieve an archived fragment.
        </p>

    </div>


    <div class="code-terminal">

        <div class="terminal-header">

            <span>
                ARCHIVE TERMINAL
            </span>

            <span>
                ● ● ●
            </span>

        </div>


        <div class="terminal-body">

            <div class="terminal-line">
                SYSTEM://CODE_ARCHIVE
            </div>

            <div class="terminal-line">
                CONNECTION: SECURE
            </div>

            <div
                id="terminalTyping"
            ></div>


            <div class="input-line">

                <span>&gt;</span>

                <input
                    id="codeInput"
                    type="password"
                    autocomplete="off"
                    spellcheck="false"
                    placeholder="ENTER ACCESS CODE"
                    onkeydown="
                        if(event.key === 'Enter')
                        checkCode()
                    "
                >

            </div>


            <button
                class="access-button"
                onclick="checkCode()"
            >
                ACCESS ARCHIVE
            </button>


            <div
                id="codeMessage"
                class="code-message"
            ></div>


            <div
                id="secretResult"
                class="secret-result"
            ></div>

        </div>

    </div>

</section>


</main>


<script>

/* =====================================================
   BOOT
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


const bootLines = [

    "USER DATABASE ........ FOUND",
    "USER RECOGNIZED ....... YES",
    "CREATOR PROFILE ....... LOADED",
    "MEMORY CHECK .......... OK",
    "CPU INITIALIZATION",
    "GRAPHICS DRIVER ....... OK",
    "AUDIO ENGINE .......... OK",
    "SCANNING MUSIC LIBRARY",
    "INDEXING PLAYLISTS",
    "VINYL EMULATION ....... OK",
    "TURNTABLE MOTOR ....... READY",
    "SOUND ARCHIVE ......... MOUNTED",
    "REFERENCE: VINYL",
    "REFERENCE: CASSETTE",
    "REFERENCE: RADIO",
    "REFERENCE: RECORD",
    "ART ENGINE ............ OK",
    "SCANNING ART ARCHIVE",
    "ANALYZING PAINTINGS",
    "CANVAS DATABASE ....... OK",
    "COLOR PALETTE ......... LOADED",
    "GALLERY SYSTEM ........ READY",
    "REFERENCE: PAINTING",
    "REFERENCE: CANVAS",
    "REFERENCE: INK",
    "REFERENCE: PHOTOGRAPHY",
    "LITERATURE ENGINE ..... OK",
    "SCANNING BOOK ARCHIVE",
    "INDEXING AUTHORS",
    "INDEXING STORIES",
    "LIBRARY CATALOG ....... OK",
    "READING MODULE ........ READY",
    "REFERENCE: BOOK",
    "REFERENCE: POETRY",
    "REFERENCE: PROSE",
    "REFERENCE: NOVEL",
    "CODE ARCHIVE .......... FOUND",
    "ENCRYPTED ENTRIES ..... FOUND",
    "CLASSIFIED DATA ....... LOADED",
    "CODE DATABASE ......... READY",
    "MEDIA ROOM CORE ....... OK",
    "ALL SYSTEMS ........... NOMINAL"
];


let bootInterval =
    setInterval(() => {

        const line =
            document.createElement(
                "div"
            );

        const random =
            bootLines[
                Math.floor(
                    Math.random() *
                    bootLines.length
                )
            ];

        line.className =
            "code-line";

        line.innerHTML =
            `<span class="code-gray">
                0x${Math.floor(
                    Math.random() *
                    999999
                )}
            </span>
            &nbsp;
            <span class="${
                random.includes("FOUND")
                ? "code-green"
                : "code-white"
            }">
                ${random}
            </span>`;

        bootCode.appendChild(line);

        if (
            bootCode.children.length > 45
        ) {
            bootCode.removeChild(
                bootCode.firstChild
            );
        }

    }, 40);


let percentage = 0;


const progressInterval =
    setInterval(() => {

        percentage +=
            Math.random() * 2.5;


        if (percentage >= 100) {

            percentage = 100;

            clearInterval(
                progressInterval
            );

            clearInterval(
                bootInterval
            );

            bootStatus.textContent =
                "SYSTEM READY";


            setTimeout(() => {

                ready.style.opacity =
                    "1";

            }, 200);


            setTimeout(() => {

                bootScreen.style.opacity =
                    "0";

                bootScreen.style.visibility =
                    "hidden";

            }, 1400);

        }


        progress.style.width =
            percentage + "%";


        if (percentage < 25) {

            bootStatus.textContent =
                "Initializing hardware...";

        } else if (
            percentage < 50
        ) {

            bootStatus.textContent =
                "Loading system drivers...";

        } else if (
            percentage < 70
        ) {

            bootStatus.textContent =
                "Mounting media devices...";

        } else if (
            percentage < 90
        ) {

            bootStatus.textContent =
                "Loading media archive...";

        } else {

            bootStatus.textContent =
                "Finalizing startup...";

        }

    }, 100);


/* =====================================================
   NAVIGATION
===================================================== */

function showSection(
    sectionID,
    button
) {

    document
        .querySelectorAll(".section")
        .forEach(
            section =>
                section.classList.remove(
                    "active"
                )
        );


    document
        .querySelectorAll(".nav-btn")
        .forEach(
            btn =>
                btn.classList.remove(
                    "active"
                )
        );


    document
        .getElementById(sectionID)
        .classList.add("active");


    button.classList.add("active");
}


/* =====================================================
   VINYL
===================================================== */

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
        "PLAYING";

}


function stopVinyl() {

    vinyl.classList.remove(
        "playing"
    );

    status.classList.remove(
        "playing"
    );

    statusText.textContent =
        "PAUSED";

}


/* =====================================================
   SPOTIFY
===================================================== */

const playlistURL =
    "https://open.spotify.com/playlist/0aFukFImzZqlBhQzskT2T3";


window.onSpotifyIframeApiReady =
    (IFrameAPI) => {

        const element =
            document.getElementById(
                "spotify-player"
            );


        IFrameAPI.createController(

            element,

            {
                width: "100%",
                height: "600",
                url: playlistURL
            },

            (EmbedController) => {

                EmbedController.addListener(
                    "playback_started",
                    () => {
                        startVinyl();
                    }
                );


                EmbedController.addListener(
                    "playback_update",
                    event => {

                        if (
                            !event ||
                            !event.data
                        ) return;


                        if (
                            event.data.isPaused
                        ) {

                            stopVinyl();

                        } else {

                            startVinyl();

                        }

                    }
                );

            }
        );

    };


/* =====================================================
   TERMINAL TYPING EFFECT
===================================================== */

const terminalTyping =
    document.getElementById(
        "terminalTyping"
    );


const terminalText =
    "AWAITING AUTHENTICATION...";


let typingIndex = 0;


function typeTerminalText() {

    if (
        typingIndex <
        terminalText.length
    ) {

        terminalTyping.textContent +=
            terminalText[
                typingIndex
            ];

        typingIndex++;

        setTimeout(
            typeTerminalText,
            45
        );

    }

}


typeTerminalText();


/* =====================================================
   SECRET CODE DATABASE
=====================================================

   IMPORTANT:

   These codes are NOT displayed
   anywhere in the interface.

===================================================== */

const secretCodes = {

    "01092018":
        "I'm having a complete gay crisis.",

    "2002":
        "Being brave doesn't mean not being afraid. Being brave means being scared, very scared, but doing what is right anyway.",

    "2003":
        "I am justice! I am the man who will save the oppressed and become the God of a new world.",

    "1996":
        "Do you like horror movies?",

    "1986":
        "We all float down here.",

    "1978":
        "He is still alive and ready to kill!",

    "1984":
        "You are all my children now.",

    "1980":
        "Here's Johnny!"

};


/* =====================================================
   CODE CHECKER
===================================================== */

function checkCode() {

    const input =
        document.getElementById(
            "codeInput"
        );

    const message =
        document.getElementById(
            "codeMessage"
        );

    const result =
        document.getElementById(
            "secretResult"
        );


    const code =
        input.value.trim();


    /* Remove previous answer */

    result.classList.remove(
        "visible"
    );

    result.innerHTML = "";


    /* Empty */

    if (!code) {

        message.textContent =
            "ERROR // NO INPUT";

        message.className =
            "code-message error";

        return;

    }


    /* Correct */

    if (
        secretCodes[code]
    ) {

        message.textContent =
            "ACCESS GRANTED // ARCHIVE DECRYPTED";

        message.className =
            "code-message success";


        /* Create secret */

        result.innerHTML = `
            <div class="scanline"></div>
            "${secretCodes[code]}"
        `;


        result.classList.add(
            "visible"
        );


        /* Clear password */

        input.value = "";


        /* Small terminal sound */

        playAccessSound();

    }


    /* Wrong */

    else {

        message.textContent =
            "ACCESS DENIED // INVALID CODE";

        message.className =
            "code-message error";


        input.select();

    }

}


/* =====================================================
   TERMINAL SOUND
===================================================== */

function playAccessSound() {

    try {

        const audio =
            new AudioContext();

        const oscillator =
            audio.createOscillator();

        const gain =
            audio.createGain();


        oscillator.frequency.value =
            880;

        oscillator.type =
            "square";


        gain.gain.setValueAtTime(
            .04,
            audio.currentTime
        );

        gain.gain.exponentialRampToValueAtTime(
            .001,
            audio.currentTime + .15
        );


        oscillator.connect(gain);

        gain.connect(
            audio.destination
        );


        oscillator.start();

        oscillator.stop(
            audio.currentTime + .15
        );

    } catch(e) {}

}

</script>

</body>
</html>
