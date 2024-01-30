<body>
  <h1>Generador de Gráficos</h1>

  <div class="left">
      <select name="" id="tipo">
          <option value="circular">
              Gráfico Circular
          </option>
          <option value="columna">
              Gráfico de Columnas
          </option>
      </select>
      <input type="text" placeholder="Título del Gráfico" id="titulo">
      <div class="datos" id="datos">
          <div class="dato">
              <input type="text" placeholder="Leyenda 1" class="serie">
              <input type="text" placeholder="Valor 1" class="valor">
          </div>
          <div class="dato">
              <input type="text" placeholder="Leyenda 2" class="serie">
              <input type="text" placeholder="Valor 2" class="valor">
          </div>
      </div>
      <button onclick="agregarDato()" class="agregar"> + </button>
      <button onclick="cargarGrafico()" class="crear-grafico">Crear Gráfico</button>
  </div>
  <div class="right">
      <div id="piechart"></div>
  </div>


  <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
  <script src="script.js"></script>
</body>