<script>
  import CircularChart from './lib/CicularChart.svelte';
  import DescripcionPerfiles from './lib/DescripcionPerfiles.svelte';
  import PorqueLosTest from './lib/PorqueLosTest.svelte';
  import TestA from './lib/TestA.svelte';
</script>

<nav class="team building">
  <ul>
    <li class="title">TEAM<br>BUILDING</li>
    <li class="subtitle">Diseñando equipos de trabajo de alto rendimiento creativo <br><span>POWERED BY marcsegarra.com</span></li>
  </ul>
</nav>

<main>
  <CircularChart />
  <DescripcionPerfiles />
  <PorqueLosTest />
  <TestA />
</main>

<style>
  main {
      overflow-y: auto; /* Habilita el scroll vertical */
      height: 100vh; /* Establece la altura máxima al 100% de la altura visible */
  }
</style>
