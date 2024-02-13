<script>
// @ts-nocheck

  import {Router,Link, Route} from 'svelte-routing';
  import CircularChart from './lib/CicularChart.svelte';
  import DescripcionPerfiles from './lib/DescripcionPerfiles.svelte';
  import PorqueLosTest from './lib/PorqueLosTest.svelte';
  import TestA from './lib/TestA.svelte';

let showTest = false;

function startTest() {
    showTest = true;
}

  document.addEventListener("DOMContentLoaded", function() {
        // Encontrar el botón
        const startTestButton = document.getElementById('start-test-btn');

        // Agregar un evento de clic al botón
        startTestButton.addEventListener('click', function() {
            // Encontrar el inicio del test (puede ser el ID de la sección donde comienza el test)
            const testStart = document.getElementById('testA');

            // Desplazarse suavemente hacia el inicio del test
            testStart.scrollIntoView({ behavior: 'smooth' });
        });
    });
</script>

<main>
  <Router>
   <nav class="team building">
      <ul>
          <li class="title">TEAM<br>BUILDING</li>
          <li class="subtitle">Diseñando equipos de trabajo de alto rendimiento creativo <br><span>POWERED BY marcsegarra.com</span></li>
      </ul>
   </nav>
   <!-- <Link to="haz el test">HAZ EL TEST</Link> -->
    <CircularChart />
    <DescripcionPerfiles />
    <PorqueLosTest />

    <!-- svelte-ignore missing-declaration -->
    <button on:click={startTest}>Haz el Test</button>

    {#if showTest}
      <TestA />
    {/if}

    <Route path= "/testA">
      <TestA />
    </Route>

  </Router>

  
</main>

<style>
  main {
      overflow-y: auto; /* Habilita el scroll vertical */
      height: 100vh; /* Establece la altura máxima al 100% de la altura visible */
  }
</style>
