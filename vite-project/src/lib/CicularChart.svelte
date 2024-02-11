<!-- CircularChart.svelte -->
<script>
  import { onMount } from 'svelte';
  import Chart from 'chart.js/auto';

  let chart;

  onMount(() => {
    // @ts-ignore
    const ctx = document.getElementById('myChart').getContext('2d');
    chart = new Chart(ctx, {
      type: 'doughnut',
      data: {
        labels: ['Rojo', 'Azul', 'Verde', 'Amarillo'],
        datasets: [{
          label: 'Resultados',
          data: [25, 25, 25, 25],
          backgroundColor: [
            '#F08080', '#F0E68C', '#90EE90', '#87CEFA'
          ],
          borderWidth: 0 // Elimina el borde
        }]
      },
      options: {
        responsive: true,
        cutout: 0, // Elimina el espacio central
        plugins: {
          legend: {
            display: false
          }
        }
      }
    });
  });
</script>

<canvas id="myChart"></canvas>

<style>
  canvas {
    aspect-ratio: auto 2560 / 598;
    position: absolute;
    left: 100px;
    height: 299px;
    width: 1280px;
  }
</style>
