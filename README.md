# gitits.github.io
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Presentación IA - GiTiTs</title>
    <style>
        /* --- ESTILOS GENERALES --- */
        :root {
            --bg-color: #121212; /* Negro casi puro */
            --text-color: #f0f0f0; /* Blanco hueso */
            --primary-color: #009688; /* Un teal conservador pero moderno */
            --primary-darker: #00796b;
            --accent-color: #FFC107; /* Amarillo para algún detalle si se necesita */
            --border-color: #333;
            --popup-bg: #222;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            line-height: 1.6;
        }

        .container {
            width: 90%;
            max-width: 900px;
            margin: 20px auto;
            padding: 20px;
            background-color: var(--bg-color); /* Podría ser ligeramente diferente si se quiere contraste */
            border-radius: 8px;
            flex-grow: 1;
        }

        h1, h2, h3 {
            color: var(--primary-color);
            margin-bottom: 15px;
        }
        
        h1 { text-align: center; font-size: 2.2em; margin-bottom: 30px;}
        h2 { font-size: 1.8em; }
        h3 { font-size: 1.4em; }

        p, ul {
            margin-bottom: 15px;
        }

        ul {
            list-style-position: inside;
            padding-left: 20px;
        }

        li {
            margin-bottom: 8px;
        }

        a {
            color: var(--primary-color);
            text-decoration: none;
        }

        a:hover {
            text-decoration: underline;
            color: var(--primary-darker);
        }

        /* --- NAVEGACIÓN PRINCIPAL (MENÚ DE TEMAS) --- */
        #main-menu {
            text-align: center;
        }

        #main-menu ul {
            list-style: none;
            padding: 0;
        }

        #main-menu li {
            margin: 15px 0;
        }

        #main-menu button {
            background-color: var(--primary-color);
            color: var(--text-color);
            border: none;
            padding: 12px 25px;
            font-size: 1.1em;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
            width: 80%;
            max-width: 400px;
        }

        #main-menu button:hover {
            background-color: var(--primary-darker);
        }

        /* --- CONTENIDO DE LOS TEMAS (DIAPOSITIVAS/ESCENAS) --- */
        .slide-content {
            display: none; /* Oculto por defecto */
        }

        .slide-content.active {
            display: block;
        }

        .scene {
            display: none; /* Oculto por defecto */
            padding: 15px;
            border: 1px solid var(--border-color);
            border-radius: 5px;
            margin-bottom: 20px;
            background-color: #1a1a1a; /* Ligeramente más claro que el fondo general */
        }

        .scene.active {
            display: block;
        }
        
        .scene-title {
            font-size: 1.5em;
            color: var(--primary-color);
            margin-bottom: 10px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 5px;
        }

        /* --- BOTONES DE NAVEGACIÓN DENTRO DE UN TEMA --- */
        .item-navigation {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 20px;
            padding-top: 15px;
            border-top: 1px solid var(--border-color);
        }

        .item-navigation button {
            background-color: var(--primary-color);
            color: var(--text-color);
            border: none;
            padding: 10px 20px;
            font-size: 1em;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .item-navigation button:hover {
            background-color: var(--primary-darker);
        }
        
        .item-navigation button:disabled {
            background-color: #555;
            cursor: not-allowed;
        }

        /* --- FOOTER --- */
        footer {
            text-align: center;
            padding: 15px;
            background-color: #0a0a0a; /* Un poco más oscuro para diferenciar */
            color: #aaa;
            font-size: 0.9em;
            width: 100%;
        }

        /* --- VENTANA EMERGENTE (POPUP) --- */
        .popup-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none; /* Oculto por defecto */
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .popup-content {
            background-color: var(--popup-bg);
            padding: 30px;
            border-radius: 8px;
            text-align: center;
            max-width: 80%;
            width: 400px;
            border: 1px solid var(--border-color);
            position: relative; /* Para el botón de cerrar */
        }

        .popup-content h3 {
            color: var(--primary-color);
            margin-top: 0;
        }
        
        .popup-content p {
            margin-bottom: 10px;
            font-size: 0.95em;
        }

        .close-popup {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 1.8em;
            color: var(--text-color);
            cursor: pointer;
            background: none;
            border: none;
        }
        
        #info-icon-container {
            text-align: right;
            margin-bottom: 10px;
        }

        #info-icon {
            font-size: 1.5em; /* Tamaño del ícono */
            cursor: pointer;
            padding: 5px;
            display: inline-block; /* Para que el padding funcione bien */
            color: var(--primary-color);
        }
         #info-icon:hover {
            color: var(--primary-darker);
        }
    </style>
</head>
<body>

    <div class="container">
        <div id="info-icon-container">
            <span id="info-icon" title="Más información sobre GiTiTs">ℹ️</span>
        </div>
        
        <!-- MENÚ PRINCIPAL DE TEMAS -->
        <div id="main-menu-container" class="slide-content active">
            <h1>🤖 Inteligencia Artificial para Chicos Pilas 🚀</h1>
            <p style="text-align:center; margin-bottom: 30px;">¡Hola a todos! Hoy vamos a parchar un ratico hablando de algo que seguro ya han escuchado: la Inteligencia Artificial, o como le dicen por ahí, la IA. Vamos a ver qué es, qué tipos hay, cómo nos afecta en el estudio (lo bueno y lo no tan bueno) y cómo podemos usarla para sacarle el jugo a la educación.</p>
            
            <nav id="main-menu">
                <ul>
                    <li><button data-target="item1">🤔 ¿Qué es una IA?</button></li>
                    <li><button data-target="item2">📚 ¿Cuáles son los tipos de IA?</button></li>
                    <li><button data-target="item3">⚖️ ¿Cómo impacta la IA a la educación? (+/-)</button></li>
                    <li><button data-target="item4">💡 ¿Cómo aprovechar la IA en la educación?</button></li>
                </ul>
            </nav>
        </div>

        <!-- ITEM 1: ¿Qué es una IA? -->
        <div id="item1" class="slide-content">
            <div class="scene-container">
                <div class="scene active">
                    <h2 class="scene-title">🤔 ¿Qué es una IA? (Parte 1)</h2>
                    <p>Imaginen que le enseñamos a las máquinas a ser un poquito como nosotros, ¡a pensar y a hacer cosas que requieren inteligencia humana!. Eso es la Inteligencia Artificial: el desarrollo de sistemas de computador que pueden hacer tareas que normalmente hacemos los humanos. Su meta es como imitar la capacidad de nuestro cerebro para resolver líos, aprender de cosas nuevas y volverse mejor con la experiencia.</p>
                    <p>Piensen en tareas como:</p>
                    <ul>
                        <li>Aprender de lo que pasa (eso se llama aprendizaje automático o Machine Learning).</li>
                        <li>Darse cuenta de lo que hay alrededor.</li>
                        <li>Razonar y tomar decisiones.</li>
                    </ul>
                </div>
                <div class="scene">
                    <h2 class="scene-title">🤔 ¿Qué es una IA? (Parte 2)</h2>
                    <p>La IA ya está metida en un montón de cosas de nuestra vida, a veces sin que nos demos cuenta, como cuando usamos ciertas apps o jugamos videojuegos. Es una tecnología que está cambiando todo.</p>
                    <p>En el colegio o la universidad, la IA está empezando a ser clave para cambiar cómo aprendemos y enseñamos. Puede ayudar a que el aprendizaje sea más personalizado, como un "profe virtual" que te ayuda cuando lo necesitas, o a que los profes puedan organizar mejor las clases.</p>
                    <p>Es bueno saber que la IA no es para reemplazar a los profes, ¡nada que ver!. Es más bien como una herramienta bacana para ayudar en el proceso de enseñanza y mejorar cómo aprendemos. Lo importante es el uso que le demos.</p>
                    <p><strong>Elemento de interés:</strong> <a href="https://www.youtube.com/watch?v=V-cZbZtjpeY&ab_channel=MOSenEspa%C3%B1ol" target="_blank" rel="noopener noreferrer">🎥 Ver video: ¿Qué es IA? (MOS en Español)</a></p>
                </div>
            </div>
            <div class="item-navigation">
                <button class="nav-btn prev-scene" disabled>◀️ Anterior</button>
                <button class="nav-btn home-btn">🏠 Inicio</button>
                <button class="nav-btn next-scene">Siguiente ▶️</button>
            </div>
        </div>

        <!-- ITEM 2: ¿Cuáles son los tipos de IA? -->
        <div id="item2" class="slide-content">
            <div class="scene-container">
                <div class="scene active">
                    <h2 class="scene-title">📚 Tipos de IA (Parte 1)</h2>
                    <p>Aunque hay muchas formas de ver esto, podemos hablar de tipos de IA según qué tan "inteligentes" son o qué pueden hacer:</p>
                    <ul>
                        <li><strong>IA Específica (o Estrecha):</strong> Piensen en una IA que es súper buena en una sola cosa, como reconocer caras en fotos o jugar ajedrez. Es experta en esa tarea específica, pero no sabe hacer nada más fuera de ese tema limitado. La mayoría de las IAs que usamos hoy son de este tipo.</li>
                    </ul>
                     <p><em>Ejemplo: El algoritmo de recomendación de YouTube o Netflix.</em></p>
                </div>
                <div class="scene">
                    <h2 class="scene-title">📚 Tipos de IA (Parte 2)</h2>
                    <ul>
                        <li><strong>IA General (o Fuerte):</strong> ¡Este es el gran reto! Es una IA que podría entender, aprender y resolver cualquier problema, así como lo hace un humano. Poder generalizar el conocimiento a muchas cosas diferentes. Esto todavía es un objetivo de investigación y estamos lejos de lograrlo.</li>
                    </ul>
                    <p><em>Ejemplo: Un robot como los de las películas de ciencia ficción que puede hacer de todo.</em></p>
                </div>
                <div class="scene">
                    <h2 class="scene-title">📚 Tipos de IA (Parte 3) - IA Generativa</h2>
                    <p>Además, ahora se habla mucho de la <strong>IA Generativa</strong>. Esta se enfoca en crear contenido nuevo y original, como escribir textos (tipo ChatGPT), hacer imágenes a partir de descripciones o incluso música. En la educación, esta IA nos puede ayudar a crear ejercicios, materiales de estudio o incluso a ayudarnos a escribir.</p>
                    <p><strong>Elemento de interés:</strong> <a href="https://www.youtube.com/watch?v=SVcsDDABEkM" target="_blank" rel="noopener noreferrer">🎥 Ver video: ¿Qué es IA Generativa? (Platzi)</a></p>
                </div>
            </div>
            <div class="item-navigation">
                <button class="nav-btn prev-scene" disabled>◀️ Anterior</button>
                <button class="nav-btn home-btn">🏠 Inicio</button>
                <button class="nav-btn next-scene">Siguiente ▶️</button>
            </div>
        </div>

        <!-- ITEM 3: ¿Cómo impacta la IA a la educación? -->
        <div id="item3" class="slide-content">
            <div class="scene-container">
                <div class="scene active">
                    <h2 class="scene-title">⚖️ Impacto de la IA en Educación (Introducción)</h2>
                    <p>La IA llegó a la educación para quedarse y tiene sus cosas buenas y sus cosas no tan buenas. ¡Vamos a verlas!</p>
                </div>
                <div class="scene">
                    <h3 class="scene-title">👍 Aspectos Positivos (¡Oportunidades!) - Parte 1</h3>
                    <ul>
                        <li><strong>Aprendizaje Personalizado:</strong> Esto es como tener un "profe a la medida". Las plataformas con IA pueden ajustar el contenido, la dificultad y el ritmo de las clases o actividades según lo que cada uno necesita y cómo va avanzando.</li>
                        <li><strong>Retroalimentación Rápida:</strong> Puedes recibir comentarios sobre tus tareas o respuestas casi de inmediato. Esto te ayuda a saber en qué te equivocaste y cómo mejorar al instante.</li>
                    </ul>
                </div>
                 <div class="scene">
                    <h3 class="scene-title">👍 Aspectos Positivos (¡Oportunidades!) - Parte 2</h3>
                    <ul>
                        <li><strong>Ayuda para Tareas del Profe:</strong> La IA puede ayudar a los profes a hacer cosas como calificar automáticamente ciertas cosas, preparar materiales o enviar comunicados a las familias para que ellos tengan más tiempo para enseñarnos y ayudarnos directamente.</li>
                        <li><strong>Desarrollo de Habilidades Bacanas:</strong> Usar IA en clase puede ayudarte a mejorar habilidades clave para el siglo XXI, como pensar críticamente, ser más creativo o resolver problemas de forma compleja.</li>
                        <li><strong>Inclusión:</strong> La IA puede ser un apoyo genial para compañeros con necesidades especiales, adaptando materiales para que sean más fáciles de usar para todos.</li>
                    </ul>
                </div>
                <div class="scene">
                    <h3 class="scene-title">👎 Aspectos Negativos (¡Desafíos!) - Parte 1</h3>
                    <ul>
                        <li><strong>Brecha Tecnológica:</strong> No todos tenemos acceso a las mismas herramientas de IA o a internet de buena calidad. Esto podría hacer que las desigualdades en la educación se hagan más grandes.</li>
                        <li><strong>Falta de Capacitación:</strong> A veces, ni los profes ni los estudiantes saben bien cómo usar estas herramientas de IA de forma efectiva.</li>
                    </ul>
                </div>
                <div class="scene">
                    <h3 class="scene-title">👎 Aspectos Negativos (¡Desafíos!) - Parte 2</h3>
                    <ul>
                        <li><strong>Temas Éticos y de Privacidad:</strong> Usar IA implica manejar datos de nosotros, los estudiantes. Hay que cuidar mucho la privacidad. También existe el riesgo de que los algoritmos de la IA tengan sesgos (como preferencias o prejuicios) que podrían ser injustos.</li>
                        <li><strong>Contenido No Siempre Confiable:</strong> La IA puede generar respuestas o información que no es correcta, está incompleta o incluso inventada. ¡Hay que estar "pilas"!</li>
                    </ul>
                </div>
                 <div class="scene">
                    <h3 class="scene-title">👎 Aspectos Negativos (¡Desafíos!) - Parte 3</h3>
                    <ul>
                        <li><strong>Riesgo de Plagio y Falta de Originalidad:</strong> Es muy fácil copiar y pegar lo que dice una IA, lo que puede afectar nuestra capacidad de pensar por nosotros mismos y ser originales.</li>
                        <li><strong>Dependencia Excesiva:</strong> Si usamos la IA para todo, podemos dejar de desarrollar habilidades importantes como el pensamiento crítico o la resolución de problemas.</li>
                    </ul>
                     <p><strong>Elemento de interés:</strong> <a href="https://www.youtube.com/watch?v=0prGmM2XCjY" target="_blank" rel="noopener noreferrer">🎥 Ver video: IA en Educación: Riesgos y Oportunidades (EDteam)</a></p>
                </div>
            </div>
            <div class="item-navigation">
                <button class="nav-btn prev-scene" disabled>◀️ Anterior</button>
                <button class="nav-btn home-btn">🏠 Inicio</button>
                <button class="nav-btn next-scene">Siguiente ▶️</button>
            </div>
        </div>

        <!-- ITEM 4: ¿Cómo fortalecer o aprovechar esos aspectos positivos? -->
        <div id="item4" class="slide-content">
            <div class="scene-container">
                <div class="scene active">
                    <h2 class="scene-title">💡 Aprovechando la IA (Parte 1)</h2>
                    <p>La IA tiene un potencial tremendo, pero depende de nosotros usarla bien. Aquí algunas ideas para aprovechar lo bueno y manejar lo no tan bueno:</p>
                    <ul>
                        <li><strong>¡Aprender Sobre IA!:</strong> No se trata solo de usarla, sino de entender cómo funciona, qué datos usa y cómo toma decisiones. Es clave que todos, profes, estudiantes y familias, sepamos de esto. Hay que "enseñar sobre IA".</li>
                        <li><strong>Pensamiento Crítico Siempre:</strong> Lo que diga una IA no es la última palabra. Hay que cuestionar, analizar y verificar la información. Usen la IA como un punto de partida, no como la respuesta final. Esto ayuda a "enseñar para la IA", desarrollando habilidades para el futuro.</li>
                    </ul>
                </div>
                <div class="scene">
                    <h2 class="scene-title">💡 Aprovechando la IA (Parte 2)</h2>
                    <ul>
                        <li><strong>Usar la IA para Crear y Aprender Mejor:</strong> En lugar de solo pedirle que haga tareas, úsenla como una herramienta para generar ideas, practicar, entender conceptos difíciles o crear proyectos originales. ¡Sean creadores con IA!. Esto es "enseñar con la IA".</li>
                        <li><strong>Ser Éticos y Responsables:</strong> Pensemos en la privacidad, los sesgos y cómo nuestras acciones al usar IA afectan a otros. Instituciones y profes deben establecer reglas claras para un uso justo y equitativo.</li>
                    </ul>
                </div>
                <div class="scene">
                    <h2 class="scene-title">💡 Aprovechando la IA (Parte 3 - Conclusión)</h2>
                    <ul>
                        <li><strong>Colaborar con los Profes:</strong> Hablen con sus profes sobre la IA, sus dudas, cómo les ayuda o qué problemas les genera. Ellos también están aprendiendo y pueden guiar el uso de estas herramientas en clase.</li>
                        <li><strong>Promover el Acceso Equitativo:</strong> Es un desafío grande, pero es crucial que se trabaje para que todos tengan las mismas oportunidades de acceder y usar la IA en educación.</li>
                    </ul>
                    <p>En resumen, la IA es una herramienta potente que puede transformar la educación, haciéndola más personalizada y efectiva. Pero para que funcione bien, necesitamos invertir en acceso, capacitación y, lo más importante, usarla de forma crítica, ética y responsable. ¡Así podremos aprovecharla para que todos aprendamos mejor y estemos listos para los retos del futuro!</p>
                </div>
            </div>
            <div class="item-navigation">
                <button class="nav-btn prev-scene" disabled>◀️ Anterior</button>
                <button class="nav-btn home-btn">🏠 Inicio</button>
                <button class="nav-btn next-scene">Siguiente ▶️</button>
            </div>
        </div>

    </div> <!-- Fin .container -->

    <footer>
        <p>Desarrollado por GiTiTs</p>
    </footer>

    <!-- VENTANA EMERGENTE DE INFORMACIÓN -->
    <div id="info-popup" class="popup-overlay">
        <div class="popup-content">
            <button class="close-popup" title="Cerrar">×</button>
            <h3>GiTiTs</h3>
            <p>Grupo de investigación tecnológica del Instituto Técnico Superior</p>
            <p>Pereira</p>
            <hr style="margin: 15px 0; border-color: var(--border-color);">
            <p><strong>Docentes:</strong></p>
            <p>Carlos Andrés Rodriguez Perez</p>
            <p>Cristian Camilo Cañaveral Avilés</p>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const menuButtons = document.querySelectorAll('#main-menu button');
            const slideContents = document.querySelectorAll('.slide-content');
            const homeButtons = document.querySelectorAll('.home-btn');
            const mainMenuContainer = document.getElementById('main-menu-container');
            
            const infoIcon = document.getElementById('info-icon');
            const popupOverlay = document.getElementById('info-popup');
            const closePopupButton = document.querySelector('.close-popup');

            let currentItemScenes = {}; // Para rastrear la escena actual de cada item

            // --- MANEJO DEL POPUP DE INFORMACIÓN ---
            infoIcon.addEventListener('click', () => {
                popupOverlay.style.display = 'flex';
            });

            closePopupButton.addEventListener('click', () => {
                popupOverlay.style.display = 'none';
            });

            popupOverlay.addEventListener('click', (e) => {
                if (e.target === popupOverlay) { // Cerrar si se hace clic fuera del contenido
                    popupOverlay.style.display = 'none';
                }
            });

            // --- FUNCIONES DE NAVEGACIÓN ---
            function showSlide(slideId) {
                slideContents.forEach(content => content.classList.remove('active'));
                const targetSlide = document.getElementById(slideId);
                if (targetSlide) {
                    targetSlide.classList.add('active');
                    
                    // Si el slide tiene escenas, inicializar y mostrar la primera
                    if (targetSlide.querySelector('.scene-container')) {
                        currentItemScenes[slideId] = 0; // Resetear a la primera escena
                        updateSceneView(slideId);
                    }
                } else {
                    // Si no se encuentra el slideId, mostrar el menú principal (fallback)
                    mainMenuContainer.classList.add('active');
                }
            }

            function updateSceneView(slideId) {
                const itemContainer = document.getElementById(slideId);
                if (!itemContainer) return;

                const scenes = itemContainer.querySelectorAll('.scene-container .scene');
                const currentSceneIndex = currentItemScenes[slideId] || 0;

                scenes.forEach((scene, index) => {
                    scene.classList.toggle('active', index === currentSceneIndex);
                });

                // Actualizar estado de botones de navegación de escena
                const prevBtn = itemContainer.querySelector('.prev-scene');
                const nextBtn = itemContainer.querySelector('.next-scene');

                if (prevBtn) prevBtn.disabled = (currentSceneIndex === 0);
                if (nextBtn) nextBtn.disabled = (currentSceneIndex === scenes.length - 1);
            }

            // --- EVENT LISTENERS PARA EL MENÚ PRINCIPAL ---
            menuButtons.forEach(button => {
                button.addEventListener('click', () => {
                    const targetId = button.getAttribute('data-target');
                    showSlide(targetId);
                });
            });

            // --- EVENT LISTENERS PARA BOTONES DE INICIO ---
            homeButtons.forEach(button => {
                button.addEventListener('click', () => {
                    showSlide('main-menu-container');
                });
            });

            // --- EVENT LISTENERS PARA NAVEGACIÓN DE ESCENAS (SIGUIENTE/ANTERIOR) ---
            document.querySelectorAll('.slide-content').forEach(itemSlide => {
                const slideId = itemSlide.id;
                const sceneContainer = itemSlide.querySelector('.scene-container');
                if (!sceneContainer) return; // No es un item con escenas

                const prevBtn = itemSlide.querySelector('.prev-scene');
                const nextBtn = itemSlide.querySelector('.next-scene');

                if (prevBtn) {
                    prevBtn.addEventListener('click', () => {
                        if (currentItemScenes[slideId] > 0) {
                            currentItemScenes[slideId]--;
                            updateSceneView(slideId);
                        }
                    });
                }

                if (nextBtn) {
                    nextBtn.addEventListener('click', () => {
                        const scenes = sceneContainer.querySelectorAll('.scene');
                        if (currentItemScenes[slideId] < scenes.length - 1) {
                            currentItemScenes[slideId]++;
                            updateSceneView(slideId);
                        }
                    });
                }
            });

            // Mostrar el menú principal al cargar
            showSlide('main-menu-container');
        });
    </script>

</body>
</html>
