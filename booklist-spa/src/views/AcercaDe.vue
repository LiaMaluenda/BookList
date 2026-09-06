<template>
  <div class="vista-acerca">
    <div class="tarjeta-acerca">
      <h2>Acerca de este proyecto</h2>
      <p>Este proyecto es el resultado de todo lo que aprendí en el módulo de Desarrollo de Interfaces Interactivas con Vue.js. Fue un gran desafío armar esta SPA (Single Page Application) desde cero y ver cómo todo se conecta.</p>
      
      <div class="caracteristicas">
        <h3>Lo que logré implementar:</h3>
        <ul>
          <li><strong>Estructura moderna:</strong> Se escribió todo usando la Composition API de Vue 3 script setup, lo que ayuda a mantener el código mucho más limpio.</li>
          <li><strong>Navegación fluida:</strong> Se usó Vue Router para moverme entre las pantallas. Logré enviar la información de cada libro directamente por la URL combinando <code>params</code> y <code>query</code>.</li>
          <li><strong>Memoria en la interfaz:</strong> Se agrególa etiqueta keep-alive para que el catálogo no se borre al entrar a ver el detalle de un libro y volver atrás.</li>
          <li><strong>Componentes ordenados:</strong> Dividí la interfaz separando las tarjetas de los libros en su propio archivo, comunicándolos con la vista principal mediante <code>props</code> y <code>emits</code>.</li>
          <li><strong>Interactividad al instante:</strong> Los formularios responden en tiempo real mientras escribes gracias a <code>v-model</code>, y capturan eventos como el "Enter" del teclado de forma completamente natural.</li>
        </ul>
      </div>
      <!-- Botón para abrir el PDF adjunto -->
      <div class="contenedor-boton-pdf">
        <a href="/resumen.pdf" target="_blank" class="btn-pdf">
           Descargar resumen del proyecto
        </a>
      </div>

      <p class="firma">Desarrollado con dedicación por Lía Maluenda.</p>
    </div>
  </div>
</template>

<script setup>
// Vista estática
</script>

<style scoped>
.vista-acerca {
  display: flex;
  justify-content: center;
}
.tarjeta-acerca {
  background: white;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 2.5rem;
  width: 100%;
  max-width: 600px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.05);
  text-align: left;
}
h2 {
  color: #2c3e50;
  margin-top: 0;
  border-bottom: 2px solid #42b883;
  padding-bottom: 0.5rem;
}
p {
  color: #444;
  line-height: 1.6;
}
.caracteristicas {
  background: #f8f9fa;
  padding: 1.5rem;
  border-radius: 6px;
  margin: 1.5rem 0;
}
h3 {
  margin-top: 0;
  color: #34495e;
  font-size: 1.1rem;
}
ul {
  padding-left: 1.5rem;
  color: #444;
  line-height: 1.8;
}
.firma {
  text-align: right;
  font-weight: bold;
  color: #42b883;
  font-size: 1.1rem;
  margin-top: 2rem;
  font-style: italic;
}
</style>