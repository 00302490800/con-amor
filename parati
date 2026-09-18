<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport"
content="width=device-width,
initial-scale=1.0,
maximum-scale=1.0,
user-scalable=no">
<meta name="apple-mobile-web-app-capable"
content="yes">
<meta name="apple-mobile-web-app-status-bar-style"
content="black-translucent">
<title>Para Melissa 🌻✨</title>
<style>
/* =====================================================
   CONFIGURACIÓN GENERAL
===================================================== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    -webkit-tap-highlight-color: transparent;
}
html,
body {
    width: 100%;
    height: 100%;
    overflow: hidden;
}
body {
    background: #020009;
    font-family:
        Georgia,
        "Times New Roman",
        serif;
    color: white;
    touch-action: manipulation;
}
/* =====================================================
   CANVAS
===================================================== */
canvas {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100%;
}
#universe {
    z-index: 1;
}
#garden {
    z-index: 2;
    pointer-events: none;
}
/* =====================================================
   CONTENIDO PRINCIPAL
===================================================== */
.content {
    position: fixed;
    inset: 0;
    z-index: 10;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    pointer-events: none;
}
/* =====================================================
   TITULO
===================================================== */
.title {
    position: absolute;
    top: 7vh;
    padding: 0 20px;
    animation:
        titleAppear 2s ease forwards;
}
.small {
    display: block;
    margin-bottom: 12px;
    font-size: 11px;
    letter-spacing: 4px;
    color: #d9c9ff;
    opacity: .85;
}
h1 {
    font-size:
        clamp(55px, 16vw, 110px);
    font-weight: normal;
    letter-spacing: 6px;
    color: #fff4bd;
    text-shadow:
        0 0 10px #ffd84d,
        0 0 25px #ff9f1c,
        0 0 50px #ff69b4,
        0 0 90px
        rgba(255,105,180,.5);
}
.subtitle {
    display: block;
    margin-top: 8px;
    font-size: 22px;
    letter-spacing: 10px;
}
/* =====================================================
   MENSAJES
===================================================== */
.message-container {
    position: absolute;
    left: 50%;
    bottom: 20vh;
    transform:
        translateX(-50%);
    width: 90%;
    max-width: 650px;
    min-height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
}
#loveMessage {
    font-size:
        clamp(18px, 4.5vw, 27px);
    line-height: 1.55;
    color: white;
    text-shadow:
        0 0 8px #ff69b4,
        0 0 20px #9d4edd;
    opacity: 0;
    transform:
        translateY(15px);
    transition:
        opacity .8s ease,
        transform .8s ease;
}
#loveMessage.show {
    opacity: 1;
    transform:
        translateY(0);
}
/* =====================================================
   BOTÓN
===================================================== */
#flowerButton {
    position: absolute;
    bottom: 8vh;
    pointer-events: auto;
    padding:
        14px 25px;
    border-radius: 50px;
    border:
        1px solid
        rgba(255,255,255,.3);
    background:
        rgba(255,255,255,.08);
    color: white;
    font-family:
        Georgia,
        serif;
    font-size: 15px;
    letter-spacing: 1px;
    backdrop-filter:
        blur(10px);
    -webkit-backdrop-filter:
        blur(10px);
    box-shadow:
        0 0 25px
        rgba(255,105,180,.2);
}
#flowerButton:active {
    transform: scale(.94);
    background:
        rgba(255,105,180,.2);
}
/* =====================================================
   INSTRUCCIÓN
===================================================== */
.instruction {
    position: absolute;
    bottom: 2.5vh;
    width: 90%;
    font-size: 10px;
    letter-spacing: 2px;
    color: #bcaee8;
    opacity: .6;
}
/* =====================================================
   ANIMACIÓN TITULO
===================================================== */
@keyframes titleAppear {
    from {
        opacity: 0;
        transform:
            translateY(-25px);
    }
    to {
        opacity: 1;
        transform:
            translateY(0);
    }
}
/* =====================================================
   IPHONE
===================================================== */
@media (max-width: 600px) {
    .title {
        top: 6vh;
    }
    .small {
        font-size: 9px;
        letter-spacing: 3px;
    }
    h1 {
        letter-spacing: 4px;
    }
    .message-container {
        bottom: 20vh;
    }
    #loveMessage {
        font-size: 19px;
        padding: 0 8px;
    }
}
/* =====================================================
   PANTALLAS MUY PEQUEÑAS
===================================================== */
@media (max-height: 700px) {
    .title {
        top: 4vh;
    }
    .message-container {
        bottom: 18vh;
    }
}
</style>
</head>
<body>
<!-- =====================================================
     UNIVERSO
===================================================== -->
<canvas id="universe"></canvas>
<!-- =====================================================
     FLORES Y PARTÍCULAS
===================================================== -->
<canvas id="garden"></canvas>
<!-- =====================================================
     TEXTO
===================================================== -->
<main class="content">
    <div class="title">
        <span class="small">
            UN PEQUEÑO UNIVERSO CREADO PARA TI
        </span>
        <h1>
            Melissa
        </h1>
        <span class="subtitle">
            🌻 ✨ 🌸
        </span>
    </div>
    <div class="message-container">
        <p id="loveMessage"></p>
    </div>
    <button id="flowerButton">
        ✨ Haz florecer el universo ✨
    </button>
    <p class="instruction">
        Toca cualquier parte de la pantalla
        para hacer aparecer una flor 🌸
    </p>
</main>
<script>
/* =====================================================
   ELEMENTOS
===================================================== */
const universe =
    document.getElementById("universe");
const garden =
    document.getElementById("garden");
const message =
    document.getElementById("loveMessage");
const button =
    document.getElementById("flowerButton");
const uctx =
    universe.getContext("2d");
const gctx =
    garden.getContext("2d");
/* =====================================================
   VARIABLES
===================================================== */
let W;
let H;
let stars = [];
let flowers = [];
let particles = [];
let phraseIndex = 0;
/* =====================================================
   FRASES PARA MELISSA ❤️
===================================================== */
const phrases = [
"Melissa, entre tantos caminos que existen en este mundo, qué bonito fue que la vida hiciera que nuestros caminos se encontraran. ❤️",
"Hay personas que llegan sin avisar y terminan convirtiéndose en una parte preciosa de nuestra historia. Tú eres esa persona para mí. 🌸",
"Si pudiera guardar un instante para siempre, escogería uno en el que pudiera verte sonreír. ✨",
"Me gusta pensar que el universo tuvo un pequeño plan cuando decidió poner tu nombre en mi historia. 🌌",
"Contigo entendí que sentirse en casa no siempre significa estar en un lugar; a veces significa estar junto a alguien. ❤️",
"Podría mirar miles de estrellas y aun así encontraría algo más bonito cuando te miro a ti. 🌟",
"Melissa, hay algo en tu sonrisa que consigue hacer más ligeros incluso aquellos días que pesan un poquito más. 🌻",
"Si mi corazón pudiera convertirse en un jardín, cada rincón tendría una flor creciendo con tu nombre. 🌷",
"Me encanta que contigo los momentos más sencillos puedan convertirse en recuerdos que quiero guardar para siempre. 💕",
"No necesito una historia perfecta; me gustaría una historia verdadera, llena de momentos que podamos llamar nuestros. ❤️",
"A veces imagino el futuro y me gusta pensar en todas las cosas bonitas que todavía nos quedan por vivir. 🌙",
"Tienes esa manera tan especial de hacer que un momento cualquiera termine convirtiéndose en uno de mis favoritos. ✨",
"Si pudiera regalarte algo que no se marchitara jamás, te regalaría un jardín entero para recordarte cuánto te quiero. 🌸",
"Melissa, quiero que siempre recuerdes que eres una persona profundamente especial para mí y que tenerte en mi vida significa muchísimo. ❤️",
"Hay sonrisas que duran unos segundos, pero se quedan en el corazón durante todo el día. La tuya es una de ellas. 🥰",
"Me gusta quererte en los pequeños detalles: en nuestras conversaciones, nuestras risas, nuestros abrazos y hasta en nuestros silencios. 💜",
"Ojalá pudiera mostrarte el cielo desde mis ojos para que pudieras ver cuántas estrellas aparecen cuando pienso en ti. 🌌",
"Tu presencia tiene una magia tranquila; no necesita hacer ruido para hacer que todo se sienta un poquito más bonito. ✨",
"Melissa, si algún día dudas de lo especial que eres, recuerda este pequeño universo: cada flor aquí nació pensando en ti. 🌻",
"No necesito que todos los días sean extraordinarios; me basta con encontrar un momento bonito contigo en ellos. ❤️",
"Qué bonito es encontrar a alguien que consigue hacer sonreír al corazón sin siquiera darse cuenta. 🌸",
"Entre todas las flores de este universo, todavía elegiría sentarme contigo y simplemente disfrutar de tu compañía. 🌙",
"Lo que siento por ti vive en los pequeños momentos: esos que quizá parecen simples, pero que para mí significan muchísimo. 💕",
"Melissa, eres uno de esos regalos inesperados de la vida que uno aprende a valorar cada día un poquito más. 🎁❤️",
"Si pudiera volver al instante en que nuestras historias se cruzaron, volvería a elegir conocerte. ✨"
];
/* =====================================================
   UTILIDAD RANDOM
===================================================== */
function random(min, max) {
    return Math.random() *
        (max - min) + min;
}
/* =====================================================
   AJUSTAR PANTALLA
===================================================== */
function resize() {
    W =
        window.innerWidth;
    H =
        window.innerHeight;
    const ratio =
        Math.min(
            window.devicePixelRatio || 1,
            2
        );
    universe.width =
        W * ratio;
    universe.height =
        H * ratio;
    garden.width =
        W * ratio;
    garden.height =
        H * ratio;
    universe.style.width =
        W + "px";
    universe.style.height =
        H + "px";
    garden.style.width =
        W + "px";
    garden.style.height =
        H + "px";
    uctx.setTransform(
        ratio,
        0,
        0,
        ratio,
        0,
        0
    );
    gctx.setTransform(
        ratio,
        0,
        0,
        ratio,
        0,
        0
    );
    createStars();
}
window.addEventListener(
    "resize",
    resize
);
/* =====================================================
   ESTRELLAS
===================================================== */
function createStars() {
    stars = [];
    const amount =
        Math.floor(
            (W * H) / 3200
        );
    for (
        let i = 0;
        i < amount;
        i++
    ) {
        stars.push({
            x:
                random(0, W),
            y:
                random(0, H),
            size:
                random(.4, 1.8),
            alpha:
                random(.2, 1),
            speed:
                random(.02, .16),
            phase:
                random(
                    0,
                    Math.PI * 2
                )
        });
    }
}
/* =====================================================
   UNIVERSO
===================================================== */
function drawUniverse(time) {
    /* Fondo */
    const background =
        uctx.createLinearGradient(
            0,
            0,
            0,
            H
        );
    background.addColorStop(
        0,
        "#010009"
    );
    background.addColorStop(
        .5,
        "#10052b"
    );
    background.addColorStop(
        1,
        "#02000a"
    );
    uctx.fillStyle =
        background;
    uctx.fillRect(
        0,
        0,
        W,
        H
    );
    /* Nebulosa */
    const nebula =
        uctx.createRadialGradient(
            W * .30,
            H * .42,
            0,
            W * .30,
            H * .42,
            W * .70
        );
    nebula.addColorStop(
        0,
        "rgba(255,60,170,.16)"
    );
    nebula.addColorStop(
        .45,
        "rgba(110,60,255,.07)"
    );
    nebula.addColorStop(
        1,
        "transparent"
    );
    uctx.fillStyle =
        nebula;
    uctx.fillRect(
        0,
        0,
        W,
        H
    );
    /* Estrellas */
    for (const star of stars) {
        star.y -= star.speed;
        if (star.y < 0) {
            star.y = H;
        }
        const pulse =
            star.alpha +
            Math.sin(
                time * .002 +
                star.phase
            ) * .25;
        uctx.beginPath();
        uctx.arc(
            star.x,
            star.y,
            star.size,
            0,
            Math.PI * 2
        );
        uctx.fillStyle =
            `rgba(255,255,255,${Math.max(.05,pulse)})`;
        uctx.fill();
    }
}
/* =====================================================
   PARTÍCULA
===================================================== */
class Particle {
    constructor(
        x,
        y,
        color
    ) {
        this.x = x;
        this.y = y;
        const angle =
            random(
                0,
                Math.PI * 2
            );
        const speed =
            random(
                .5,
                3.5
            );
        this.vx =
            Math.cos(angle) *
            speed;
        this.vy =
            Math.sin(angle) *
            speed;
        this.life = 1;
        this.size =
            random(
                1,
                3.5
            );
        this.color =
            color;
    }
    update() {
        this.x += this.vx;
        this.y += this.vy;
        this.vx *= .97;
        this.vy *= .97;
        this.life -= .018;
    }
    draw() {
        gctx.save();
        gctx.globalAlpha =
            Math.max(
                0,
                this.life
            );
        gctx.shadowBlur =
            15;
        gctx.shadowColor =
            this.color;
        gctx.fillStyle =
            this.color;
        gctx.beginPath();
        gctx.arc(
            this.x,
            this.y,
            this.size,
            0,
            Math.PI * 2
        );
        gctx.fill();
        gctx.restore();
    }
}
/* =====================================================
   CLASE FLOR
===================================================== */
class Flower {
    constructor(
        x,
        y,
        size,
        type
    ) {
        this.x = x;
        this.y = y;
        this.size = size;
        this.type = type;
        this.phase =
            random(
                0,
                Math.PI * 2
            );
        this.rotation =
            random(
                0,
                Math.PI * 2
            );
    }
    draw(time) {
        const movement =
            Math.sin(
                time * .001 +
                this.phase
            ) * 5;
        gctx.save();
        gctx.translate(
            this.x,
            this.y + movement
        );
        gctx.rotate(
            this.rotation
        );
        if (
            this.type ===
            "sunflower"
        ) {
            drawSunflower(
                this.size
            );
        }
        if (
            this.type ===
            "carnation"
        ) {
            drawCarnation(
                this.size
            );
        }
        if (
            this.type ===
            "alstroemeria"
        ) {
            drawAlstroemeria(
                this.size
            );
        }
        gctx.restore();
    }
}
/* =====================================================
   GIRASOL 🌻
===================================================== */
function drawSunflower(size) {
    const petals = 18;
    for (
        let i = 0;
        i < petals;
        i++
    ) {
        const angle =
            i *
            Math.PI *
            2 /
            petals;
        gctx.save();
        gctx.rotate(
            angle
        );
        const gradient =
            gctx.createLinearGradient(
                0,
                -size,
                0,
                0
            );
        gradient.addColorStop(
            0,
            "#fff36b"
        );
        gradient.addColorStop(
            .5,
            "#ffc928"
        );
        gradient.addColorStop(
            1,
            "#e88900"
        );
        gctx.fillStyle =
            gradient;
        gctx.shadowBlur =
            15;
        gctx.shadowColor =
            "#ffb300";
        gctx.beginPath();
        gctx.ellipse(
            0,
            -size * .55,
            size * .18,
            size * .55,
            0,
            0,
            Math.PI * 2
        );
        gctx.fill();
        gctx.restore();
    }
    /* Centro */
    gctx.shadowBlur =
        20;
    gctx.shadowColor =
        "#8b4513";
    gctx.fillStyle =
        "#54240b";
    gctx.beginPath();
    gctx.arc(
        0,
        0,
        size * .27,
        0,
        Math.PI * 2
    );
    gctx.fill();
    /* Semillas */
    gctx.fillStyle =
        "#d99b38";
    for (
        let i = 0;
        i < 20;
        i++
    ) {
        const angle =
            i * 2.4;
        const radius =
            size * .18;
        gctx.beginPath();
        gctx.arc(
            Math.cos(angle) *
            radius,
            Math.sin(angle) *
            radius,
            1.5,
            0,
            Math.PI * 2
        );
        gctx.fill();
    }
}
/* =====================================================
   CLAVEL 🌸
===================================================== */
function drawCarnation(size) {
    const colors = [
        "#ff4f91",
        "#ff72ad",
        "#ff9ac5",
        "#e91e63",
        "#ffc1dc"
    ];
    for (
        let i = 0;
        i < 55;
        i++
    ) {
        const angle =
            random(
                0,
                Math.PI * 2
            );
        const radius =
            random(
                size * .15,
                size * .85
            );
        gctx.save();
        gctx.rotate(
            angle
        );
        gctx.fillStyle =
            colors[
                Math.floor(
                    Math.random() *
                    colors.length
                )
            ];
        gctx.globalAlpha =
            .85;
        gctx.beginPath();
        gctx.moveTo(
            0,
            0
        );
        gctx.quadraticCurveTo(
            random(
                -size * .4,
                size * .4
            ),
            -radius * .4,
            random(
                -size * .4,
                size * .4
            ),
            -radius
        );
        gctx.quadraticCurveTo(
            random(
                -size * .4,
                size * .4
            ),
            -radius * .6,
            0,
            0
        );
        gctx.fill();
        gctx.restore();
    }
    gctx.globalAlpha =
        1;
    gctx.fillStyle =
        "#ffbfd9";
    gctx.shadowBlur =
        20;
    gctx.shadowColor =
        "#ff4f91";
    gctx.beginPath();
    gctx.arc(
        0,
        0,
        size * .15,
        0,
        Math.PI * 2
    );
    gctx.fill();
}
/* =====================================================
   ASTROMELIA 💜
===================================================== */
function drawAlstroemeria(size) {
    const petals = 6;
    for (
        let i = 0;
        i < petals;
        i++
    ) {
        const angle =
            i *
            Math.PI *
            2 /
            petals;
        gctx.save();
        gctx.rotate(
            angle
        );
        const gradient =
            gctx.createLinearGradient(
                0,
                0,
                0,
                -size
            );
        gradient.addColorStop(
            0,
            "#ffffff"
        );
        gradient.addColorStop(
            .3,
            "#e9b7ff"
        );
        gradient.addColorStop(
            1,
            "#9b5de5"
        );
        gctx.fillStyle =
            gradient;
        gctx.shadowBlur =
            15;
        gctx.shadowColor =
            "#c77dff";
        gctx.beginPath();
        gctx.moveTo(
            0,
            0
        );
        gctx.bezierCurveTo(
            -size * .4,
            -size * .2,
            -size * .35,
            -size * .85,
            0,
            -size
        );
        gctx.bezierCurveTo(
            size * .35,
            -size * .85,
            size * .4,
            -size * .2,
            0,
            0
        );
        gctx.fill();
        gctx.restore();
    }
    /* Manchas */
    gctx.fillStyle =
        "#7b2cbf";
    for (
        let i = 0;
        i < 8;
        i++
    ) {
        const angle =
            random(
                0,
                Math.PI * 2
            );
        const radius =
            random(
                size * .25,
                size * .65
            );
        gctx.beginPath();
        gctx.arc(
            Math.cos(angle) *
            radius,
            Math.sin(angle) *
            radius,
            2,
            0,
            Math.PI * 2
        );
        gctx.fill();
    }
    /* Centro */
    gctx.fillStyle =
        "#ffd166";
    gctx.shadowBlur =
        15;
    gctx.shadowColor =
        "#ffd166";
    gctx.beginPath();
    gctx.arc(
        0,
        0,
        size * .12,
        0,
        Math.PI * 2
    );
    gctx.fill();
}
/* =====================================================
   CREAR FLOR
===================================================== */
function createFlower(
    x,
    y
) {
    const types = [
        "sunflower",
        "carnation",
        "alstroemeria"
    ];
    const type =
        types[
            Math.floor(
                Math.random() *
                types.length
            )
        ];
    const size =
        random(
            30,
            65
        );
    flowers.push(
        new Flower(
            x,
            y,
            size,
            type
        )
    );
    let particleColor;
    if (
        type ===
        "sunflower"
    ) {
        particleColor =
            "#ffd43b";
    }
    if (
        type ===
        "carnation"
    ) {
        particleColor =
            "#ff5c9d";
    }
    if (
        type ===
        "alstroemeria"
    ) {
        particleColor =
            "#c084fc";
    }
    for (
        let i = 0;
        i < 30;
        i++
    ) {
        particles.push(
            new Particle(
                x,
                y,
                particleColor
            )
        );
    }
}
/* =====================================================
   FRASES
===================================================== */
function showPhrase() {
    message.classList.remove(
        "show"
    );
    setTimeout(
        () => {
            message.textContent =
                phrases[
                    phraseIndex
                ];
            message.classList.add(
                "show"
            );
            phraseIndex++;
            if (
                phraseIndex >=
                phrases.length
            ) {
                phraseIndex = 0;
            }
        },
        400
    );
}
/* =====================================================
   INTERACCIÓN
===================================================== */
function interact(
    x,
    y
) {
    createFlower(
        x,
        y
    );
    showPhrase();
}
/* =====================================================
   TOQUE EN PANTALLA
===================================================== */
window.addEventListener(
    "pointerdown",
    function(event) {
        if (
            event.target ===
            button
        ) {
            return;
        }
        interact(
            event.clientX,
            event.clientY
        );
    }
);
/* =====================================================
   BOTÓN
===================================================== */
button.addEventListener(
    "click",
    function() {
        const x =
            random(
                W * .15,
                W * .85
            );
        const y =
            random(
                H * .35,
                H * .75
            );
        interact(
            x,
            y
        );
    }
);
/* =====================================================
   ANIMACIÓN
===================================================== */
function animate(
    time
) {
    uctx.clearRect(
        0,
        0,
        W,
        H
    );
    gctx.clearRect(
        0,
        0,
        W,
        H
    );
    drawUniverse(
        time
    );
    /* Flores */
    for (
        const flower
        of flowers
    ) {
        flower.rotation +=
            .0005;
        flower.draw(
            time
        );
    }
    /* Partículas */
    for (
        let i =
            particles.length - 1;
        i >= 0;
        i--
    ) {
        particles[i].update();
        particles[i].draw();
        if (
            particles[i].life <= 0
        ) {
            particles.splice(
                i,
                1
            );
        }
    }
    requestAnimationFrame(
        animate
    );
}
/* =====================================================
   INICIO
===================================================== */
resize();
/* Flores iniciales */
flowers.push(
    new Flower(
        W * .17,
        H * .73,
        48,
        "sunflower"
    ),
    new Flower(
        W * .39,
        H * .77,
        43,
        "carnation"
    ),
    new Flower(
        W * .61,
        H * .71,
        47,
        "alstroemeria"
    ),
    new Flower(
        W * .83,
        H * .76,
        44,
        "sunflower"
    )
);
/* Primera frase */
showPhrase();
/* Iniciar universo */
requestAnimationFrame(
    animate
);
</script>
</body>
			</html>