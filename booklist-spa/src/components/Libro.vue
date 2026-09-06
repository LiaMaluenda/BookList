<template>
  <article class="item-libro">
    <h3>{{ libro.titulo }}</h3>
    <p><strong>Autor:</strong> {{ libro.autor }}</p>
    <p><strong>Categoría:</strong> {{ libro.categoria }}</p>
    
    <!-- Uso de v-show para la descripción (Lección 2) -->
    <p v-show="libro.descripcion" class="descripcion"><em>{{ libro.descripcion }}</em></p>
    
    <div class="grupo-botones">
      <button @click="$emit('ver', libro)" class="btn-info">Ver Detalle</button>
      <button @click="$emit('eliminar', libro.id)" class="btn-borrar">Eliminar</button>
      
      <!-- Uso del modificador .once (Lección 4) -->
      <button @click.once="marcarFavorito" class="btn-fav">{{ textoFavorito }}</button>
    </div>
  </article>
</template>

<script setup>
import { ref } from 'vue'

// Recibe los datos usando v-bind (Lección 2)
defineProps({
  libro: Object
})

defineEmits(['ver', 'eliminar'])

const textoFavorito = ref('⭐ Destacar')

const marcarFavorito = () => {
  textoFavorito.value = '🌟 Destacado'
}
</script>

<style scoped>
.item-libro {
  border: 1px solid #eaeaea;
  padding: 1.5rem;
  border-radius: 8px;
  background: white;
}
.descripcion {
  font-size: 0.9rem;
  color: #7f8c8d;
}
.grupo-botones {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 1rem;
}
button { padding: 0.5rem; border: none; border-radius: 4px; cursor: pointer; flex: 1; color: white;}
.btn-info { background: #3498db; }
.btn-borrar { background: #e74c3c; }
.btn-fav { background: #f1c40f; color: #333; }
</style>