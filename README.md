<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>MEDIA ROOM</title>

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
    font-family: Arial, Helvetica, sans-serif;
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

    font-family: "Courier New", monospace;

    display: flex;
    flex-direction: column;

    padding: 30px;

    overflow: hidden;

    transition:
        opacity .8s ease,
        visibility .8s ease;
}

.boot-top {
    display: flex;
    justify-content: space-between;
    align-items: center;

    border-bottom: 1px solid #333;

    padding-bottom: 12px;
    margin-bottom: 20px;

    font-size: 13px;
}

.boot-logo {
    font-size: 18px;
    font-weight: bold;
    letter-spacing: 2px;
}

#boot-code {
    flex: 1;
    overflow: hidden;

    font-size: 12px;
    line-height: 1.55;

    color: #aaa;
}

.code-line {
    white-space: nowrap;
}

.code-gray {
    color: #666;
}

.code-white {
    color: #ddd;
}

.code-green {
    color: #79ff79;
}

.code-blue {
    color: #8bbcff;
}

.code-yellow {
    color: #d9d16c;
}

.boot-bottom {
    border-top: 1px solid #333;

    padding-top: 18px;
    margin-top: 15px;
}

#boot-status {
    margin-top: 12px;
    font-size: 13px;
}

.progress-container {
    width: 100%;
    height: 14px;

    border: 1px solid #555;

    margin-top: 12px;
    padding: 2px;
}

#progress {
    width: 0%;
    height: 100%;

    background: #ddd;

    transition: width .1s linear;
}

.cursor {
    display: inline-block;

    width: 8px;
    height: 14px;

    background: #ddd;

    animation: blink .8s infinite;

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
   SYSTEM READY
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

    transition: opacity .5s ease;
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

    padding: 18px 30px;

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

    flex-wrap: wrap;
}

.nav-btn {
    border: none;

    color: #aaa;

    background: transparent;

    padding: 10px 15px;

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

    padding: 50px 0;
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


/* =====================================================
   VINYL LABEL
===================================================== */

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


/* =====================================================
   TURNTABLE ARM
===================================================== */

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

    transition: .2s;
}

.book-button:hover {
    background: white;

    color: black;
}


/* =====================================================
   CODE ARCHIVE
===================================================== */

.code-grid {
    display: grid;

    grid-template-columns:
        repeat(
            auto-fit,
            minmax(280px, 1fr)
        );

    gap: 25px;
}

.secret-code {
    position: relative;

    min-height: 260px;

    padding: 28px;

    background:
        linear-gradient(
            145deg,
            #151515,
            #080808
        );

    border:
        1px solid
        rgba(255,255,255,.09);

    border-radius: 18px;

    overflow: hidden;

    transition:
        transform .3s,
        border-color .3s,
        box-shadow .3s;
}

.secret-code::before {
    content: "CLASSIFIED";

    position: absolute;

    top: 15px;
    right: -35px;

    transform:
        rotate(35deg);

    font-family:
        "Courier New",
        monospace;

    font-size: 9px;

    letter-spacing: 3px;

    color: #333;
}

.secret-code:hover {
    transform:
        translateY(-7px);

    border-color:
        rgba(255,255,255,.25);

    box-shadow:
        0 20px 50px
        rgba(0,0,0,.6);
}

.code-number {
    font-family:
        "Courier New",
        monospace;

    font-size: 28px;

    letter-spacing: 4px;

    color: #ddd;
}

.code-line-decoration {
    margin:
        15px 0 25px;

    color: #444;

    font-family:
        "Courier New",
        monospace;
}

.secret-code p {
    color: #bbb;

    font-family:
        Georgia,
        serif;

    font-size: 17px;

    line-height: 1.6;

    font-style: italic;
}

.secret-code span {
    position: absolute;

    bottom: 20px;
    left: 28px;

    font-family:
        "Courier New",
        monospace;

    font-size: 9px;

    letter-spacing: 2px;

    color: #555;
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

        padding: 9px 6px;
    }

    .spotify-layout {
        grid-template-columns: 1fr;
    }

    .spotify-window {
        height: 600px;
    }

    #boot-screen {
        padding: 18px;
    }

    #boot-code {
        font-size: 10px;
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
            🎵 Music
        </button>

        <button
            class="nav-btn"
            onclick="showSection('art', this)"
        >
            🎨 Art
        </button>

        <button
            class="nav-btn"
            onclick="showSection('books', this)"
        >
            📚 Books
        </button>

        <button
            class="nav-btn"
            onclick="showSection('codes', this)"
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

        <h1>
            Music
        </h1>

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


<!-- =====================================================
     CODE ARCHIVE
===================================================== -->

<section
    id="codes"
    class="section"
>

    <div class="section-header">

        <h1>
            Code Archive
        </h1>

        <p>
            Classified fragments recovered from the media archive.
        </p>

    </div>


    <div class="code-grid">


        <article class="secret-code">

            <div class="code-number">
                01092018
            </div>

            <div class="code-line-decoration">
                ─────────────────
            </div>

            <p>
                "I'm having a complete gay crisis."
            </p>

            <span>
                ARCHIVE ENTRY // 001
            </span>

        </article>


        <article class="secret-code">

            <div class="code-number">
                2002
            </div>

            <div class="code-line-decoration">
                ─────────────────
            </div>

            <p>
                "Being brave doesn't mean not being afraid.
                Being brave means being scared, very scared,
                but doing what is right anyway."
            </p>

            <span>
                ARCHIVE ENTRY // 002
            </span>

        </article>


        <article class="secret-code">

            <div class="code-number">
                2003
            </div>

            <div class="code-line-decoration">
                ─────────────────
            </div>

            <p>
                "I am justice! I am the man who will save
                the oppressed and become the God of a new world."
            </p>

            <span>
                ARCHIVE ENTRY // 003
            </span>

        </article>


        <article class="secret-code">

            <div class="code-number">
                1996
            </div>

            <div class="code-line-decoration">
                ─────────────────
            </div>

            <p>
                "Do you like horror movies?"
            </p>

            <span>
                ARCHIVE ENTRY // 004
            </span>

        </article>


        <article class="secret-code">

            <div class="code-number">
                1986
            </div>

            <div class="code-line-decoration">
                ─────────────────
            </div>

            <p>
                "We all float down here."
            </p>

            <span>
                ARCHIVE ENTRY // 005
            </span>

        </article>


        <article class="secret-code">

            <div class="code-number">
                1978
            </div>

            <div class="code-line-decoration">
                ─────────────────
            </div>

            <p>
                "He is still alive and ready to kill!"
            </p>

            <span>
                ARCHIVE ENTRY // 006
            </span>

        </article>


        <article class="secret-code">

            <div class="code-number">
                1984
            </div>

            <div class="code-line-decoration">
                ─────────────────
            </div>

            <p>
                "You are all my children now."
            </p>

            <span>
                ARCHIVE ENTRY // 007
            </span>

        </article>


        <article class="secret-code">

            <div class="code-number">
                1980
            </div>

            <div class="code-line-decoration">
                ─────────────────
            </div>

            <p>
                "Here's Johnny!"
            </p>

            <span>
                ARCHIVE ENTRY // 008
            </span>

        </article>


    </div>

</section>


</main>


<script>

/* =====================================================
   BOOT DATABASE
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


const codeFragments = [

    /* USER */

    "0x00008A21  USER DATABASE .......... FOUND",

    "0x00009142  USER RECOGNIZED ......... YES",

    "0x00009C81  CREATOR PROFILE ........ LOADED",

    "0x0000A112  PERSONAL MEDIA ......... FOUND",

    "0x0000B482  USER PREFERENCES ....... LOADED",


    /* SYSTEM */

    "0x0000A4F2  SYSTEM_INIT",

    "0x0000B81C  MEMORY CHECK ........ OK",

    "0x0000C920  CPU INITIALIZATION",

    "0x0000D118  GRAPHICS DRIVER ..... OK",

    "0x0000EFA2  AUDIO ENGINE ........ OK",


    /* MUSIC */

    "0x0001A882  ANALYZING AUDIO FILES",

    "0x0001B901  SCANNING MUSIC LIBRARY",

    "0x0001C442  DETECTING ALBUMS",

    "0x0001D781  INDEXING PLAYLISTS",

    "0x0001E902  VINYL EMULATION ....... OK",

    "0x00020A11  TURNTABLE MOTOR ....... READY",

    "0x00021D90  FREQUENCY ANALYSIS .... OK",

    "0x00022FA1  SOUND ARCHIVE ......... MOUNTED",

    "0x000231B8  REFERENCE: VINYL",

    "0x00024AA1  REFERENCE: CASSETTE",

    "0x00025BC2  REFERENCE: RADIO",

    "0x00026DA8  REFERENCE: RECORD",

    "0x00028A10  DAFT PUNK ARCHIVE ...... FOUND",

    "0x00029C77  PINK FLOYD INDEX ....... FOUND",

    "0x0002AE18  NIRVANA RECORDS ........ FOUND",

    "0x0002B991  TWENTY ONE PILOTS ...... FOUND",


    /* ART */

    "0x0002C812  ART ENGINE ............ OK",

    "0x0002D551  SCANNING ART ARCHIVE",

    "0x0002E118  ANALYZING PAINTINGS",

    "0x0002F204  CANVAS DATABASE ........ OK",

    "0x000301A8  COLOR PALETTE .......... LOADED",

    "0x00031291  VISUAL ARCHIVE ......... MOUNTED",

    "0x00032AA1  GALLERY SYSTEM ......... READY",

    "0x00033B82  REFERENCE: PAINTING",

    "0x00034C11  REFERENCE: CANVAS",

    "0x00035D90  REFERENCE: INK",

    "0x00036FA1  REFERENCE: PHOTOGRAPHY",

    "0x000371A8  REFERENCE: FILM",

    "0x000382C1  MODERN ART COLLECTION .. FOUND",

    "0x00039411  PAINTING DATABASE ...... FOUND",

    "0x0003A882  SKETCH ARCHIVE ......... FOUND",


    /* LITERATURE */

    "0x0003B901  LITERATURE ENGINE ...... OK",

    "0x0003CA42  SCANNING BOOK ARCHIVE",

    "0x0003DB18  INDEXING AUTHORS",

    "0x0003EC77  INDEXING STORIES",

    "0x0003FD91  TEXT DATABASE .......... READY",

    "0x00040A11  LIBRARY CATALOG ........ OK",

    "0x00041B82  READING MODULE ......... READY",

    "0x00042C90  REFERENCE: BOOK",

    "0x00043DA1  REFERENCE: POETRY",

    "0x00044F18  REFERENCE: PROSE",

    "0x00045A81  REFERENCE: NOVEL",

    "0x00046B92  REFERENCE: SHORT STORY",

    "0x00047C18  NOVEL DATABASE ......... FOUND",

    "0x00048DA2  POETRY ARCHIVE ......... FOUND",

    "0x00049F11  LITERARY INDEX ......... FOUND",


    /* CODE ARCHIVE */

    "0x00053A21  CODE ARCHIVE .......... FOUND",

    "0x00054B82  ENCRYPTED ENTRIES ...... FOUND",

    "0x00055C91  CLASSIFIED DATA ........ LOADED",

    "0x00056D18  CODE DATABASE .......... READY",

    "0x00057E81  ARCHIVE INTEGRITY ...... OK",


    /* FINAL */

    "0x0004EF81  MEDIA ROOM CORE ........ OK",

    "0x0004FA22  MUSIC MODULE ........... READY",

    "0x00050B91  ART MODULE ............. READY",

    "0x00051C18  LITERATURE MODULE ...... READY",

    "0x00052D81  ALL MEDIA SYSTEMS ...... NOMINAL"

];


/* =====================================================
   TERMINAL
===================================================== */

function addCodeLine() {

    const line =
        document.createElement(
            "div"
        );


    const random =
        codeFragments[
            Math.floor(
                Math.random() *
                codeFragments.length
            )
        ];


    const number =
        Math.floor(
            Math.random() *
            0xFFFFFF
        )
        .toString(16)
        .toUpperCase();


    let className =
        "code-white";


    if (
        random.includes(
            "FOUND"
        )
    ) {

        className =
            "code-green";

    }


    if (
        random.includes(
            "REFERENCE"
        )
    ) {

        className =
            "code-blue";

    }


    if (
        random.includes(
            "WARNING"
        )
    ) {

        className =
            "code-yellow";

    }


    line.className =
        "code-line";


    line.innerHTML =

        `<span class="code-gray">
            0x${number}
        </span>
        &nbsp;
        <span class="${className}">
            ${random}
        </span>`;


    bootCode.appendChild(
        line
    );


    if (
        bootCode.children.length
        > 45
    ) {

        bootCode.removeChild(
            bootCode.firstChild
        );

    }

}


let codeInterval =
    setInterval(
        addCodeLine,
        42
    );


/* =====================================================
   PROGRESS
===================================================== */

let percent = 0;


const progressInterval =
    setInterval(
        () => {

            percent +=
                Math.random() * 2.8;


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


                setTimeout(
                    () => {

                        ready.style.opacity =
                            "1";

                    },
                    250
                );


                setTimeout(
                    () => {

                        bootScreen.style.opacity =
                            "0";

                        bootScreen.style.visibility =
                            "hidden";

                    },
                    1500
                );

            }


            progress.style.width =
                percent + "%";


            if (
                percent < 20
            ) {

                bootStatus.textContent =
                    "Initializing hardware...";

            }

            else if (
                percent < 40
            ) {

                bootStatus.textContent =
                    "Loading system drivers...";

            }

            else if (
                percent < 60
            ) {

                bootStatus.textContent =
                    "Mounting media devices...";

            }

            else if (
                percent < 80
            ) {

                bootStatus.textContent =
                    "Loading Music / Art / Literature...";

            }

            else if (
                percent < 95
            ) {

                bootStatus.textContent =
                    "Loading classified archive...";

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
   SPOTIFY + VINYL
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

            (
                EmbedController
            ) => {


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
