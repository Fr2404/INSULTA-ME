<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Haz clic o presiona cualquier tecla para recibir los insultos más absurdos, divertidos y originales de internet. ¡Entra bajo tu propio riesgo!">
    <meta name="keywords" content="insultame, generador de insultos, frases divertidas, insultos graciosos, web absurda">
    <meta name="robots" content="index, follow">
    <link rel="canonical" href="https://tu-enlace-de-github-o-vercel.com">

    <!-- SEO para Redes Sociales -->
    <meta property="og:title" content="Insúltame - Generador de Insultos Absurdos">
    <meta property="og:description" content="Haz clic para recibir los insultos más originales y divertidos.">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://tu-enlace-de-github-o-vercel.com">
    
    <style>
        * {
            box-sizing: border-box;
        }
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Courier New', Courier, monospace;
            background-color: #f0f0f0;
            user-select: none;
            overflow: hidden; 
            padding: 20px;
        }

        h1 {
            font-size: 3.5rem;
            text-transform: uppercase;
            font-weight: bold;
            color: #333;
            pointer-events: none;
            text-align: center;
            margin: 0 0 20px 0;
        }

        /* BOTÓN EXCLUSIVO PARA MÓVILES */
        .btn-movil {
            display: block;
            padding: 15px 30px;
            font-size: 1.2rem;
            font-family: inherit;
            font-weight: bold;
            background-color: #000;
            color: #fff;
            border: none;
            box-shadow: 4px 4px 0px #888;
            cursor: pointer;
            z-index: 10;
            -webkit-tap-highlight-color: transparent; /* Quita el destello azul al tocar */
        }
        .btn-movil:active {
            transform: translate(2px, 2px);
            box-shadow: 2px 2px 0px #888;
        }

        /* Estilos base para los popups */
        .popup-random {
            position: absolute;
            padding: 12px 18px;
            background: white;
            border: 3px solid #000;
            box-shadow: 5px 5px 0px #000;
            font-weight: bold;
            font-size: 1rem;
            max-width: 85vw; /* Asegura que no se desborde del ancho del móvil */
            z-index: 100;
            pointer-events: none;
            animation: aparecer 0.1s ease-out;
        }

        /* --- DISEÑO EXCLUSIVO PARA PC (PANTALLAS GRANDES) --- */
        @media (min-width: 768px) {
            body {
                cursor: pointer; /* Solo el PC invita a hacer clic en el fondo */
            }
            h1 {
                font-size: 7rem;
                margin: 0;
            }
            .btn-movil {
                display: none; /* Escondemos el botón en ordenadores */
            }
            .popup-random {
                font-size: 1.2rem;
                max-width: 350px;
            }
        }

        @keyframes aparecer {
            from { transform: scale(0.5); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }
    </style>
</head>
<body>

    <h1>INSULTA ME</h1>
    
    <!-- Este botón solo se mostrará en teléfonos y tablets -->
    <button class="btn-movil" id="btnInsulto">¡PÚLSAME, IDIOTA!</button>

    <script>
        const frasesRandom = [
            "🧠 Tu cerebro está en perfecto estado, principalmente porque nunca lo usas.",
            "🛡️ Eres inmune a la telepatía. No hay nada que leer ahí dentro.",
            "🕯️ Das tanta luz como una vela apagada debajo de una mesa.",
            "🎭 El mundo es un teatro, pero tu papel es de árbol secundario.",
            "📉 Si la mediocridad pagara impuestos, tú salvarías la economía del país.",
            "🧬 Tu árbol genealógico debe ser un círculo perfecto.",
            "🧱 Tienes la asombrosa capacidad de disminuir el coeficiente intelectual de cualquier habitación en la que entras.",
            "🦧 No me decepcionas, porque para eso primero tendría que haber esperado algo de ti.",
            "🩹 Eres como una tirita usada: molesto de ver y nadie te quiere cerca.",
            "🪫 Tu batería social está baja, pero tu nivel de interés general está en números negativos.",
            "♟️ Juegas al ajedrez mental contigo mismo y logras perder en dos movimientos.",
            "🤡 Eres la prueba viviente de que los errores de la simulación pueden llegar muy lejos.",
            "🚰 Eres tan emocionante como un vaso de agua del grifo tibia.",
            "🧭 Estás buscando el sentido del ridículo, pero se te ha roto la brújula.",
            "🎈 Tu mayor talento es ocupar espacio y consumir oxígeno.",
            "👾 Error 404: Cerebro no encontrado.",
            "🍀 Has ganado 0 euros. ¡Felicidades!",
            "🧘 Respira hondo... y sigue haciendo clics, idiota.",
            "🗑️ Tu opinión es como el correo no deseado: va directa a la papelera sin abrir.",
            "🪞 Si yo fuera tú, demandaría a mis padres por la configuración por defecto.",
            "🦚 Presumes tanto que parece que tienes algo que ocultar... además de tu inteligencia.",
            "🧴 Por gente como tú, el champú viene con instrucciones de uso.",
            "👕 Eres la razón por la que las planchas de ropa llevan la etiqueta de 'no planchar con la prenda puesta'.",
            "📱 Eres más inútil que la E de Vodafone.",
            "🍄 Eres más feo que la G de gnomo.",
            "🐊 Eres más inútil que la E de Lacoste.",
            "🧠 Eres más feo que la P de psicólogo.",
            "🦏 Eres más feo que una nevera por detrás.",
            "🦇 Tienes menos luces que una cueva.",
            "⛵ Tienes menos luces que la patera de un contrabandista.",
            "🦓 Tienes menos futuro que el sastre de Tarzán.",
            "✈️ Tienes menos papeles que el visado de Aladdín.",
            "🎪 Tienes menos gracia que un lunes por la mañana.",
            "🦷 Eres más feo que el Fary chupando un limón.",
            "🧊 Eres más frío que el abrazo de una suegra.",
            "🐌 Eres más lento que el caballo del malo.",
            "🦘 Tienes menos estabilidad mental que un canguro en una cama elástica.",
        ];

        const coloresRandom = ["#ffeb3b", "#ff5722", "#e91e63", "#9c27b0", "#00bcd4", "#4caf50", "#ff9800"];

        function crearPopup(x, y) {
            const popup = document.createElement('div');
            popup.className = 'popup-random';
            
            popup.innerText = frasesRandom[Math.floor(Math.random() * frasesRandom.length)];
            popup.style.backgroundColor = coloresRandom[Math.floor(Math.random() * coloresRandom.length)];

            // Lo inyectamos primero para poder medirlo en tiempo real
            document.body.appendChild(popup);

            const anchoPopup = popup.offsetWidth;
            const altoPopup = popup.offsetHeight;

            let posX, posY;

            // DETECCIÓN: Si no hay coordenadas válidas o es una pantalla móvil pequeña
            if (x === undefined || y === undefined || window.innerWidth < 768) {
                // En móvil los tiramos en la mitad superior de la pantalla de forma aleatoria controlada
                posX = Math.random() * (window.innerWidth - anchoPopup - 20) + 10;
                posY = Math.random() * (window.innerHeight * 0.45 - altoPopup) + 20; 
            } else {
                // En PC sigue la punta del ratón
                posX = x;
                posY = y;

                // Evitar que el popup se desborde por los límites derecho o inferior en PC
                if (posX + anchoPopup > window.innerWidth) posX = window.innerWidth - anchoPopup - 20;
                if (posY + altoPopup > window.innerHeight) posY = window.innerHeight - altoPopup - 20;
            }

            // Forzar márgenes mínimos de seguridad generales
            if (posX < 10) posX = 10;
            if (posY < 10) posY = 10;

            popup.style.left = `${posX}px`;
            popup.style.top = `${posY}px`;

            // Animación de salida y limpieza de memoria
            setTimeout(() => {
                popup.style.transition = "opacity 0.3s ease";
                popup.style.opacity = "0";
                setTimeout(() => popup.remove(), 300);
            }, 3000);
        }

        // --- DISPOSITIVOS MÓVILES ---
        const boton = document.getElementById('btnInsulto');
        
        // El evento 'touchstart' responde inmediatamente en pantallas táctiles sin lag
        boton.addEventListener('touchstart', (e) => {
            e.stopPropagation(); // Evita que el evento "haga eco" hacia el fondo
            crearPopup();
        });
        
        // Respaldar con click ordinario para móviles por si usan emuladores
        boton.addEventListener('click', (e) => {
            e.stopPropagation();
            if (window.innerWidth < 768) crearPopup();
        });

        // --- ORDENADORES (PC) ---
        window.addEventListener('click', (e) => {
            // Solo se activa el clic de fondo si estamos en una pantalla de PC
            if (window.innerWidth >= 768) {
                crearPopup(e.clientX, e.clientY);
            }
        });

        // Evento de teclado funcional para PCs
        window.addEventListener('keydown', () => {
            crearPopup();
        });
    </script>

</body>
</html>
