<template>
  <div class="vista-detalle">
    <div class="tarjeta-informacion">
      <h2>Ficha del Libro #{{ idLibro }}</h2>
      <ul class="datos-lista">
        <li><strong>Título:</strong> {{ datosQuery.titulo }}</li>
        <li><strong>Autor:</strong> {{ datosQuery.autor }}</li>
        <li><strong>Categoría:</strong> {{ datosQuery.categoria }}</li>
      </ul>
      <button @click="regresar" class="btn-regresar">Regresar al catálogo</button>
    </div>
  </div>
</template>


<script setup>
import { useRoute, useRouter } from 'vue-router'

const route = useRoute()
const router = useRouter()

const idLibro = Number(route.params.id)
const datosQuery = {
  titulo: route.query.titulo,
  autor: route.query.autor,
  categoria: route.query.categoria
}

const regresar = () => {
  router.push('/libros')
}
</script>


<style scoped>
.vista-detalle {
  display: flex;
  justify-content: center;
}
.tarjeta-informacion {
  background: white;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 2rem;
  width: 100%;
  max-width: 500px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.05);
}
.datos-lista {
  list-style: none;
  padding: 0;
  margin: 1.5rem 0;
}
.datos-lista li {
  margin-bottom: 0.8rem;
  font-size: 1.1rem;
}
.btn-regresar {
  width: 100%;
  background: #2c3e50;
  color: white;
  border: none;
  padding: 0.8rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
}
</style>