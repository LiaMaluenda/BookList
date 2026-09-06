<template>
  <div class="contenedor-principal">
    <nav class="barra-navegacion">
      <router-link to="/">Inicio</router-link>
      <router-link to="/libros">Catálogo</router-link>
      <router-link to="/acerca-de">Acerca de</router-link>
    </nav>
    <main class="contenido-vista">
      <router-view v-slot="{ Component }">
        <keep-alive>
          <component :is="Component" />
        </keep-alive>
      </router-view>
    </main>
  </div>
</template>

<script setup>
// Contenedor principal de rutas con keep-alive
</script>

<style scoped>
.contenedor-principal {
  font-family: system-ui, -apple-system, sans-serif;
  margin: 0;
  padding: 0;
}
.barra-navegacion {
  background-color: #1a1a1a;
  padding: 1rem;
  display: flex;
  gap: 1rem;
  justify-content: center;
}
.barra-navegacion a {
  color: white;
  text-decoration: none;
  font-weight: 600;
}
.barra-navegacion a.router-link-active {
  color: #42b883;
}
.contenido-vista {
  padding: 2rem;
  max-width: 1000px;
  margin: 0 auto;
}
</style>