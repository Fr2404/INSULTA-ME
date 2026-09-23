<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Insúltame - Generador de Insultos Absurdos online</title>
    <meta name="description" content="Haz clic o presiona cualquier tecla para recibir los insultos más absurdos, divertidos y originales de internet. ¡Entra bajo tu propio riesgo!">
    <meta name="keywords" content="insultame, generador de insultos, frases divertidas, insultos graciosos, web absurda">
    <meta name="robots" content="index, follow">
    <link rel="canonical" href="https://tu-enlace-de-hosting.com">
    <!-- SEO para Redes Sociales -->
    <meta property="og:title" content="Insúltame - Generador de Insultos Absurdos">
    <meta property="og:description" content="Haz clic para recibir los insultos más originales y divertidos.">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://tu-enlace-de-hosting.com">
    
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
            cursor: pointer;
            touch-action: manipulation; 
        }

        h1 {
            font-size: 4rem;
            text-transform: uppercase;
            font-weight: bold;
            color: #333;
            pointer-events: none;
            text-align: center;
            margin: 0;
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
            max-width: 85vw;
            z-index: 100;
            pointer-events: none;
            animation: aparecer 0.1s ease-out;
        }

        /* DISEÑO PARA PC */
        @media (min-width: 768px) {
            h1 {
                font-size: 8rem;
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

<script>
    // --- GENERADOR NATIVO DE SONIDO "PLUP" ---
    function reproducirPlup() {
        try {
            // Creamos el contexto de audio nativo
            const AudioContext = window.AudioContext || window.webkitAudioContext;
            const ctx = new AudioContext();
            
            const osc = ctx.createOscillator();
            const ganancia = ctx.createGain();
            
            osc.connect(ganancia);
            ganancia.connect(ctx.destination);
            
            // Frecuencia tipo burbuja ("plup"): empieza grave y sube rápido
            osc.type = 'sine';
            osc.frequency.setValueAtTime(150, ctx.currentTime); 
            osc.frequency.exponentialRampToValueAtTime(600, ctx.currentTime + 0.08); 
            
            // Volumen rápido que desaparece en milisegundos
            ganancia.gain.setValueAtTime(0.3, ctx.currentTime);
            ganancia.gain.exponentialRampToValueAtTime(0.01, ctx.currentTime + 0.08);
            
            osc.start(ctx.currentTime);
            osc.stop(ctx.currentTime + 0.08);
        } catch (e) {
            console.log("Audio no soportado o bloqueado");
        }
    }

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
        // Ejecuta el "plup" sintético al instante
        reproducirPlup();

        const popup = document.createElement('div');
        popup.className = 'popup-random';
        
        popup.innerText = frasesRandom[Math.floor(Math.random() * frasesRandom.length)];
        popup.style.backgroundColor = coloresRandom[Math.floor(Math.random() * coloresRandom.length)];

        document.body.appendChild(popup);

        const anchoPopup = popup.offsetWidth;
        const altoPopup = popup.offsetHeight;

        let posX, posY;

        if (x === undefined || y === undefined) {
            posX = Math.random() * (window.innerWidth - anchoPopup - 20) + 10;
            posY = Math.random() * (window.innerHeight - altoPopup - 20) + 10;
        } else {
            posX = x - (anchoPopup / 2);
            posY = y - (altoPopup / 2);

            if (posX < 10) posX = 10;
            if (posY < 10) posY = 10;
            if (posX + anchoPopup > window.innerWidth - 10) posX = window.innerWidth - anchoPopup - 10;
            if (posY + altoPopup > window.innerHeight - 10) posY = window.innerHeight - altoPopup - 10;
        }

        popup.style.left = `${posX}px`;
        popup.style.top = `${posY}px`;

        setTimeout(() => {
            popup.style.transition = "opacity 0.3s ease";
            popup.style.opacity = "0";
            setTimeout(() => popup.remove(), 300);
        }, 1500);
    }

    window.addEventListener('touchstart', (e) => {
        const toque = e.touches[0];
        crearPopup(toque.clientX, toque.clientY);
    });

    window.addEventListener('click', (e) => {
        if (e.pointerType === 'touch') return; 
        crearPopup(e.clientX, e.clientY);
    });

    window.addEventListener('keydown', (e) => {
        if (e.repeat) return; 
        crearPopup();
    });
</script>

</body>
</html>
