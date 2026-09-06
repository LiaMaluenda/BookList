<template>
  <div class="vista-inicio">
    <h1>Sistema de Gestión BookList</h1>

    <div v-if="!sesionIniciada" class="caja-registro">
      <p>Ingresa tu nombre para acceder al sistema:</p>
      <input 
        v-model="nombreUsuario" 
        @keyup.enter="iniciarSesion" 
        type="text" 
        placeholder="Escribe tu nombre..." 
      />
      <button @click="iniciarSesion" class="btn-comenzar">Comenzar</button>
    </div>

    <div v-else>
      <h2 class="saludo">¡Hola, {{ nombreUsuario }}!</h2>
      <p>Administra el inventario literario de forma eficiente y centralizada.</p>
      
      <div class="grupo-acciones-inicio">
        <div class="caja-contador">
          <p>Libros gestionados en esta sesión: <strong>{{ contador }}</strong></p>
          <button @click="aumentarContador" class="btn-contador">Sumar libro gestionado</button>
        </div>
        
        <div class="caja-navegacion">
          <button @click="irAlCatalogo" class="btn-ir-catalogo">Ir al Catálogo ➔</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const nombreUsuario = ref('')
const sesionIniciada = ref(false)
const contador = ref(0)

const iniciarSesion = () => {
  if (nombreUsuario.value.trim() !== '') {
    sesionIniciada.value = true
  }
}

const aumentarContador = () => {
  contador.value++
}

const irAlCatalogo = () => {
  router.push('/libros')
}
</script>

<style scoped>
.vista-inicio {
  text-align: center;
  margin-top: 50px;
}
h1 {
  font-size: 2.5rem;
  color: #2c3e50;
  margin-bottom: 0.5rem;
}
.caja-registro {
  margin-top: 2rem;
  padding: 2rem;
  background: #f5f5f5;
  border-radius: 8px;
  display: inline-block;
}
.caja-registro input {
  padding: 0.8rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-right: 10px;
  outline: none;
}
.caja-registro input:focus {
  border-color: #42b883;
}
.btn-comenzar {
  background: #42b883;
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
}
.btn-comenzar:hover {
  background: #33a06f;
}
.saludo {
  color: #42b883;
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
}
p {
  color: #666;
  font-size: 1.2rem;
}
.grupo-acciones-inicio {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
  margin-top: 2rem;
}
.caja-contador {
  padding: 1.5rem;
  background: #f8f9fa;
  border-radius: 8px;
  border: 1px solid #eaeaea;
  width: 100%;
  max-width: 400px;
}
.btn-contador {
  margin-top: 1rem;
  background: #3498db;
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  width: 100%;
}
.btn-contador:hover {
  background: #2980b9;
}
.caja-navegacion {
  width: 100%;
  max-width: 400px;
}
.btn-ir-catalogo {
  background: #2c3e50;
  color: white;
  border: none;
  padding: 1rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1.1rem;
  width: 100%;
  font-weight: bold;
}
.btn-ir-catalogo:hover {
  background: #1a252f;
}
</style>