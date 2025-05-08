<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carta CSS Animada Mejorada</title>
    <style>
        body {
            background: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }
        .flowers {
            position: absolute;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            z-index: 0;
        }
        .flower {
            position: absolute;
            width: 40px;
            height: 40px;
            animation: float 3s infinite ease-in-out; /* antes 6s, ahora 3s */
        }
        .flower .petal {
            position: absolute;
            width: 16px;
            height: 24px;
            background: #ffb6c1;
            border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
            transform-origin: bottom center;
        }
        .flower .petal1 { transform: rotate(0deg) translateY(-12px);}
        .flower .petal2 { transform: rotate(72deg) translateY(-12px);}
        .flower .petal3 { transform: rotate(144deg) translateY(-12px);}
        .flower .petal4 { transform: rotate(216deg) translateY(-12px);}
        .flower .petal5 { transform: rotate(288deg) translateY(-12px);}
        .flower .center {
            position: absolute;
            top: 12px;
            left: 12px;
            width: 16px;
            height: 16px;
            background: #ffd700;
            border-radius: 50%;
            z-index: 1;
            box-shadow: 0 0 8px #ffd70088;
        }
        /* Animaciones de las flores */
        @keyframes float {
            0% { transform: translateY(0) scale(1);}
            50% { transform: translateY(-30px) scale(1.1);}
            100% { transform: translateY(0) scale(1);}
        }
        .flower.f1 { left: 10vw; top: 20vh; animation-delay: 0s;}
        .flower.f2 { left: 80vw; top: 25vh; animation-delay: 1s;}
        .flower.f3 { left: 20vw; top: 70vh; animation-delay: 2s;}
        .flower.f4 { left: 70vw; top: 80vh; animation-delay: 1.5s;}
        .flower.f5 { left: 50vw; top: 10vh; animation-delay: 0.5s;}
        .flower.f6 { left: 30vw; top: 40vh; animation-delay: 2.5s;}
        .flower.f7 { left: 60vw; top: 60vh; animation-delay: 1.2s;}
        .envelope {
            position: relative;
            width: 320px;
            height: 220px;
            background: #d32f2f;
            border: 2px solid #b71c1c;
            border-radius: 10px;
            box-shadow: 0 8px 24px rgba(0,0,0,0.12), 0 0 40px 10px #ffb6c144;
            overflow: hidden;
            cursor: pointer;
            transition: box-shadow 0.5s cubic-bezier(.77,0,.18,1);
            z-index: 2;
        }
        .envelope:hover {
            box-shadow: 0 12px 32px rgba(0,0,0,0.18), 0 0 60px 20px #ffb6c1aa;
        }
        .envelope.open {
            box-shadow: 0 16px 40px rgba(0,0,0,0.22), 0 0 80px 30px #ffd70088;
        }
        .flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 110px;
            background: #b71c1c;
            clip-path: polygon(0 0, 50% 100%, 100% 0);
            transform-origin: top center;
            transition: transform 0.7s cubic-bezier(.77,0,.18,1);
            z-index: 2;
        }
        .envelope.open .flap {
            transform: rotateX(-120deg);
        }
        .envelope::after {
            content: '';
            position: absolute;
            bottom: -110px;
            left: 0;
            width: 100%;
            height: 110px;
            background: #b71c1c;
            clip-path: polygon(0 100%, 50% 0, 100% 100%);
            z-index: 3;
        }

        .envelope.open .letter {
            top: 10px; /* sube la hoja, pero no se distorsiona */
            opacity: 1;
            pointer-events: auto;
        }
        .letter-content {
            padding: 10px 20px;
            font-family: 'Segoe UI', Arial, sans-serif;
            color: #b71c1c;
            font-size: 1.1rem;
            text-align: center;
            line-height: 1.5;
            animation: fadeIn 1s;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px);}
            to { opacity: 1; transform: translateY(0);}
        }
        /* Corazones animados */
        .heart {
            position: absolute;
            width: 24px;
            height: 24px;
            background: #eb2f2c;
            transform: rotate(40deg);
            animation: heartFloat 6s infinite ease-in-out;
        }

        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 24px;
            height: 24px;
            background: #eb2f2c;
            border-radius: 50%;
        }

        .heart::before {
            top: -10px;
            left: 0;
        }

        .heart::after {
            left: -12px;
            top: 0;
        }

/* Animación flotante */
@keyframes heartFloat {
    0% {
        transform: translateY(0) rotate(45deg);
        opacity: 1;
    }
    100% {
        transform: translateY(-100px) rotate(45deg);
        opacity: 0;
    }
}

/* Posiciones y demoras */
.heart.h1 { left: 15vw; top: 60vh; animation-delay: 0s; }
.heart.h2 { left: 85vw; top: 65vh; animation-delay: 1.5s; }
.heart.h3 { left: 60vw; top: 90vh; animation-delay: 3s; }
.heart.h4 { left: 30vw; top: 70vh; animation-delay: 2.2s; }
.heart.h5 { left: 50vw; top: 50vh; animation-delay: 4s; }


        @keyframes heartFloat {
            0% { transform: translateY(0) scale(1);}
            50% { transform: translateY(-40px) scale(1.1);}
            100% { transform: translateY(0) scale(1);}
        }

        /* Haz que las flores extra tengan pétalos y centro */
        .flower.f8, .flower.f9, .flower.f10, .flower.f11, .flower.f12 {
            width: 32px;
            height: 32px;
        }
        .flower.f8 .petal, .flower.f9 .petal, .flower.f10 .petal, .flower.f11 .petal, .flower.f12 .petal {
            width: 12px;
            height: 18px;
        }
        .flower.f8 .center, .flower.f9 .center, .flower.f10 .center, .flower.f11 .center, .flower.f12 .center {
            width: 10px;
            height: 10px;
            top: 8px;
            left: 8px;
        }
    </style>
</head>
<body>
    <div class="flowers">
        <div class="flower f1">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f2">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f3">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f4">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f5">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f6">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f7">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <!-- Flores adicionales -->
        <div class="flower f8" style="left:5vw;top:80vh;animation-delay:1.7s;">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f9" style="left:90vw;top:60vh;animation-delay:2.2s;">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f10" style="left:40vw;top:15vh;animation-delay:0.8s;">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f11" style="left:75vw;top:10vh;animation-delay:1.1s;">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <div class="flower f12" style="left:15vw;top:50vh;animation-delay:2.8s;">
            <div class="petal petal1"></div>
            <div class="petal petal2"></div>
            <div class="petal petal3"></div>
            <div class="petal petal4"></div>
            <div class="petal petal5"></div>
            <div class="center"></div>
        </div>
        <!-- Corazones animados -->
        <div class="heart h1"></div>
        <div class="heart h2"></div>
        <div class="heart h3"></div>
        <div class="heart h4"></div>
        <div class="heart h5"></div>
    </div>
    <div class="envelope" id="envelope">
        <div class="flap"></div>
        <div class="letter">


            </div>
        </div>
    </div>
    <script>
        const envelope = document.getElementById('envelope');
        envelope.addEventListener('click', () => {
            // Si quieres animación antes de ir a la otra página, espera un poco:
            envelope.classList.add('open');
            setTimeout(() => {
                window.location.href = 'hoja.html'; // Cambia por el nombre de tu página
            }, 800); // 800ms para que se vea la animación de abrir
        });
    </script>
</body>
</html>
