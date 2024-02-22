<script>
    let rounds = [
        {
            questions: [
                "Prefiero estar conmigo mismo o tener relaciones persona-persona.",
                "Prefiero estar rodeado de varias personas, me gusta la interrelación dentro de los grupos.",
                "Prefiero la profundidad de las experiencias a su variedad.",
                "Prefiero la variedad de experiencias a la profundidad de cada una.",
                "Prefiero guardarme mis propios pensamientos si no me los preguntan directamente.",
                "Me gusta compartir mis pensamientos con otras personas.",
                "Me gusta especialmente la quietud y la tranquilidad y un buen nivel de intimidad.",
                "Me siento cómodo con un cierto nivel de bullicio y en los eventos sociales.",
                "Funciono especialmente bien cuando tengo tiempo para mí mismo y reflexionar.",
                "Funciono especialmente bien cuando puedo compartir ideas con otras personas.",
                "Tengo un círculo reducido de amistades de mucho tiempo, y soy cauto cuando conozco a alguien por primera vez.",
                "Tengo un círculo amplio de amistades, mucha facilidad para hacer.",
                "Utilizo la intuición como principal manera de tomar decisiones.",
                "Utilizo la lógica y el análisi racional como principal manera de tomar decisiones.",
                "Me gusta ser cortés con los demás, y tener en cuenta sus sentimientos al comunicarme con ellos.",
                "Me gustan decir las cosas como son, tanto si gustan como si no.",
                "Empleo argumentos emocionales y personales para convencer a los demás.",
                "Empleo los argumentos lógicos y objetivos para convencer a los demás.",
                "Prefiero la comunicación con el contexto de las situaciones, y las implicaciones personales de las mismas.",
                "Prefiero la comunicación concisa, concreta y orientada a las tareas o cuestiones objetivas.",
                "Tengo facilidad para expresar emociones.",
                "No suelo expresar emociones.",
                "Lo más importante es que la gente comprenda el por qué de las decisiones, los motivos y valores que la han inspirado.",
                "Lo más importante es que la gente entienda lo que hay que hacer, y el para qué, es decir el objetivo que se persigue.",
            ],
            options: [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5]
        }
    ];

    let currentRound = 0;
    let currentQuestions = [0, 1]; // Índices de las preguntas actuales en cada ronda
    let answers = Array(rounds.length).fill([null, null]); // Almacenamiento de respuestas

    function handleNextQuestion() {
        if (currentQuestions[0] < rounds[currentRound].questions.length - 2) {
            currentQuestions[0] += 2;
            currentQuestions[1] += 2;
        } else {
            currentRound++;
            currentQuestions = [0, 1]; // Reiniciar índices para la siguiente ronda
        }
    }

    function handleAnswerSelection(option, index) {
        answers[currentRound][index] = option;
    }
</script>

<main>
    <h1>Test de Personalidad</h1>
    {#if currentRound < rounds.length}
        <h2>Round {currentRound + 1}</h2>
        <form on:submit|preventDefault={handleNextQuestion}>
            <div class="question-container">
                {#each currentQuestions as questionIndex, index}
                    <div class="question-box">
                        <div class="question">
                            <h3>
                                {rounds[currentRound].questions[questionIndex]}
                            </h3>
                        </div>
                    </div>
                {/each}
            </div>
            <div class="options-container">
                {#each rounds[currentRound].options as option}
                    <button 
                        class:option-selected={answers[currentRound][0] === option || answers[currentRound][1] === option}
                        on:click={() => handleAnswerSelection(option, 0)}
                        style="font-family: 'sansation', sans-serif; font-size: 24px; width: 60px; height: 60px; border-radius: 50%; display: flex; justify-content: center; align-items: center;">
                        {option}
                    </button>
                {/each}
            </div>
            <button type="submit">Siguiente</button>
        </form>
    {:else}
        <p class="blink">Test completado.</p>
    {/if}
</main>

<style>

    main{
        padding: 20px;
    }

    h1 {
        font-family: 'sansation', sans-serif;
        font-size: 60px;
    }

    h3 {
        font-family: 'sansation', sans-serif;
        font-size: 40px;
        margin: 0; /* Eliminar márgenes internos */
    }

    .question-container {
        display: flex;
        flex-wrap: wrap; /* Permitir que las preguntas se envuelvan si no caben en una línea */
        justify-content: space-between; /* Distribuir las preguntas horizontalmente */
        padding: 0 20px; /* Margen izquierdo y derecho */
    }

    .question-box {
        background-color: #cbcaca; 
        border: 2px solid #605f5f; /* Borde rectangular */
        border-radius: 5px; /* Bordes redondeados */
        padding: 20px; /* Espaciado interno */
        margin-bottom: 20px; /* Margen inferior */
        flex: 0 1 calc(48% - 20px); /* Calculamos el ancho de la pregunta */
    }

    .options-container {
        display: flex;
        justify-content: center;
        margin-top: 20px;
    }

    button {
        margin: 5px;
        background-color: #e0e0e0;
        border: none;
        cursor: pointer;
    }

    button[type="submit"] {
        font-size: 24px; /* Tamaño de la fuente */
        width: 200px; /* Ancho del botón */
        height: 80px; /* Alto del botón */
        border-radius: 10px; /* Bordes redondeados */
        background-color: #4CAF50; /* Color de fondo */
        color: white; /* Color del texto */
        border: none; /* Sin borde */
        cursor: pointer; /* Cursor apuntador */
        transition: background-color 0.3s; /* Transición suave del color de fondo */
    }

    button[type="submit"]:hover {
        background-color: #45a049; /* Cambio de color de fondo al pasar el mouse */
    }

    button.option-selected {
        box-shadow: 0px 0px 10px 5px rgba(0,0,0,0.75); 
    }

    p {
        font-family: 'sansation', sans-serif;
        font-size: 40px;
    }

    @keyframes blink-animation {
        0% { opacity: 1; }
        50% { opacity: 0; }
        100% { opacity: 1; }
    }

    .blink {
        animation: blink-animation 1s infinite; 
    }
</style>
