<!-- QuestionnaireChart.svelte -->
<script>
    import { onMount, onDestroy } from 'svelte';
    import Chart from 'chart.js/auto';
  
    let chart;
    let scores = []; // Aquí almacenaremos los puntajes de las respuestas
  

    // Calcula el puntaje total
    function calculateTotalScore() {
      let total = 0;
      for (let i = 0; i < questions.length; i++) {
        total += scores[i] || 0; // Asegúrate de sumar 0 si no hay puntaje para la pregunta
      }
      return total;
    }
  
    onMount(() => {
      // @ts-ignore
      const ctx = document.getElementById('myChart').getContext('2d');
  
      chart = new Chart(ctx, {
        type: 'doughnut',
        data: {
          labels: ['Rojo', 'Azul', 'Verde', 'Amarillo'],
          datasets: [{
            label: 'Resultados',
            data: [0, 0, 0, 0], // Inicializamos con valores predeterminados
            backgroundColor: [
              'rgba(255, 99, 132, 0.2)',
              'rgba(54, 162, 235, 0.2)',
              'rgba(75, 192, 192, 0.2)',
              'rgba(255, 206, 86, 0.2)'
            ],
            borderColor: [
              'rgba(255, 99, 132, 1)',
              'rgba(54, 162, 235, 1)',
              'rgba(75, 192, 192, 1)',
              'rgba(255, 206, 86, 1)'
            ],
            borderWidth: 1
          }]
        },
        options: {
          responsive: true
        }
      });
    });
  
    onDestroy(() => {
      if (chart) {
        chart.destroy();
      }
    });
  
    // Actualiza el gráfico cuando cambian los puntajes
    $: {
      const totalScore = calculateTotalScore();
      updateChart(totalScore);
    }
  
    function updateChart(totalScore) {
      // Actualiza los datos del gráfico
      if (chart) {
        if (totalScore <= -10) {
          chart.data.datasets[0].data = [1, 0, 0, 0]; // Rojo
        } else if (totalScore >= -9 && totalScore <= 9) {
          chart.data.datasets[0].data = [0, 1, 0, 0]; // Azul
        } else if (totalScore >= 10 && totalScore <= 29) {
          chart.data.datasets[0].data = [0, 0, 1, 0]; // Verde
        } else if (totalScore >= 30) {
          chart.data.datasets[0].data = [0, 0, 0, 1]; // Amarillo
        }
        chart.update();
      }
    }
  </script>
  
  <canvas id="myChart" width="400" height="400"></canvas>
  
  <!-- <style>
    canvas {
      max-width: 100%;
      max-height: 100%;
    }
  </style> -->
  