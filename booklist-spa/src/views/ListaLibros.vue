<template>
  <section class="seccion-catalogo">
    <h2>Catálogo de Libros</h2>
    
    <form @submit.prevent="registrarLibro" class="formulario-registro">
      <div class="inputs-superiores">
        <input v-model="formulario.titulo" type="text" placeholder="Título" required />
        <input v-model="formulario.autor" type="text" placeholder="Autor" required />
        <select v-model="formulario.categoria" required>
          <option value="" disabled>Categoría...</option>
          <option value="Novela">Novela</option>
          <option value="Ensayo">Ensayo</option>
          <option value="Biografía">Biografía</option>
        </select>
      </div>
      
      <textarea 
        v-model="formulario.descripcion" 
        @keyup.enter="registrarLibro" 
        placeholder="Breve sinopsis (Presiona Enter para guardar)" 
        rows="2"
      ></textarea>
      
      <button type="submit">Guardar Libro</button>
    </form>

    <div class="vista-previa" v-if="formulario.titulo || formulario.autor">
      <strong>Agregando:</strong> {{ formulario.titulo }} <span v-if="formulario.autor">- por {{ formulario.autor }}</span>
    </div>

    <div v-if="libros.length === 0" class="alerta-vacia">
      No existen registros en la base de datos.
    </div>

    <div v-else class="cuadricula-libros">
      <Libro 
        v-for="libro in libros" 
        :key="libro.id" 
        :libro="libro" 
        @ver="navegarDetalle" 
        @eliminar="borrarLibro" 
      />
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import Libro from '../components/Libro.vue'

const router = useRouter()

const libros = ref([
  { id: 1, titulo: 'Cien años de soledad', autor: 'Gabriel García Márquez', categoria: 'Novela', descripcion: 'La saga de la familia Buendía.' }
])

const formulario = ref({
  titulo: '',
  autor: '',
  categoria: '',
  descripcion: ''
})

const registrarLibro = () => {
  if(!formulario.value.titulo || !formulario.value.autor) return;

  const nuevoId = libros.value.length > 0 
    ? Math.max(...libros.value.map(l => l.id)) + 1 
    : 1
    
  libros.value.push({
    id: nuevoId,
    titulo: formulario.value.titulo,
    autor: formulario.value.autor,
    categoria: formulario.value.categoria,
    descripcion: formulario.value.descripcion
  })
  
  formulario.value = { titulo: '', autor: '', categoria: '', descripcion: '' }
}

const borrarLibro = (idBusqueda) => {
  libros.value = libros.value.filter(l => l.id !== idBusqueda)
}

const navegarDetalle = (libroData) => {
  router.push({
    path: `/libros/${libroData.id}`,
    query: {
      titulo: libroData.titulo,
      autor: libroData.autor,
      categoria: libroData.categoria,
      descripcion: libroData.descripcion
    }
  })
}
</script>


<style scoped>
.seccion-catalogo {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
.formulario-registro {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  background: #f5f5f5;
  padding: 1.5rem;
  border-radius: 8px;
}
.inputs-superiores {
  display: flex;
  gap: 1rem;
}
.inputs-superiores input, .inputs-superiores select {
  flex: 1;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}
textarea {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}
.formulario-registro button {
  background: #42b883;
  color: white;
  border: none;
  padding: 0.8rem;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
.vista-previa {
  background: #e8f5e9;
  padding: 0.8rem;
  border-radius: 4px;
  color: #2e7d32;
  font-size: 0.9rem;
}
.cuadricula-libros {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}
.alerta-vacia {
  text-align: center;
  color: #7f8c8d;
  padding: 2rem;
  background: #fdfdfd;
  border: 1px dashed #ccc;
}
</style>