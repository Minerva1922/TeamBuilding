<!-- TestA.svelte -->
<script>
    let rounds = [
        {
            questions: [
                {
                    question1: "Prefiero estar conmigo mismo o tener relaciones persona-persona.",
                    question2: "Prefiero estar rodeado de varias personas, me gusta la interrelación dentro de los grupos."
                },
                {
                    question1: "Prefiero la profundidad de las experiencias a su variedad.",
                    question2: "Prefiero la variedad de experiencias a la profundidad de cada una."
                },
                {
                    question1: "Prefiero guardarme mis propios pensamientos si no me los preguntan directamente.",
                    question2: "Me gusta compartir mis pensamientos con otras personas."
                },
                {
                    question1: "Me gusta especialmente la quietud y la tranquilidad y un buen nivel de intimidad.",
                    question2: "Me siento cómodo con un cierto nivel de bullicio y en los eventos sociales."
                },
                {
                    question1: "Funciono especialmente bien cuando tengo tiempo para mí mismo y reflexionar.",
                    question2: "Funciono especialmente bien cuando puedo compartir ideas con otras personas."
                },
                {
                    question1: "Tengo un círculo reducido de amistades de mucho tiempo, y soy cauto cuando conozco a alguien por primera vez.",
                    question2: "Tengo un círculo amplio de amistades, mucha facilidad para hacer."
                },
            ],
            options: [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5]
        }
    ];

    let currentRound = 0;
    let currentQuestion = 0;
    let answers = [];

    function handleNextQuestion() {
        if (currentQuestion === 0) {
            currentQuestion = 1;
        } else {
            currentQuestion = 0;
            if (currentRound < rounds.length - 1) {
                currentRound += 1;
            } else {
                // El usuario ha completado todas las rondas, calcular resultados o mostrarlos
            }
        }
    }

    function handleAnswerSelection(option) {
        answers[currentRound] = option;
    }
</script>

<main>
    <h1>Test de Personalidad</h1>
    {#if currentRound < rounds.length}
        <h2>Round {currentRound + 1}</h2>
        <form on:submit|preventDefault={handleNextQuestion}>
            <h3>{rounds[currentRound].questions[currentQuestion].question1}</h3>
            <h3>{rounds[currentRound].questions[currentQuestion].question2}</h3>
            <button type="submit">{currentQuestion === 0 ? 'Siguiente pregunta' : 'Siguiente pregunta'}</button>
        </form>
        <div class="options-container">
            {#each rounds[currentRound].options as option}
                <button 
                    class="option-button"
                    class:selected={answers[currentRound] === option}
                    on:click={() => handleAnswerSelection(option)}>
                    {option}
                </button>
            {/each}
        </div>
    {:else}
        <p>Test completado.</p>
    {/if}
</main>

<style>
    .options-container {
        display: flex;
        flex-wrap: wrap;
    }

    .option-button {
        margin-right: 10px;
        margin-bottom: 10px;
    }
</style>
