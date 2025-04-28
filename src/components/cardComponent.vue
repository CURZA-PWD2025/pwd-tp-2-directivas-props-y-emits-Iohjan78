<template>
    <div class="card">
        <h2>Titulo: {{ movie.titulo }}</h2>
        <p>Id: {{ movie.id }}</p>
        <p>Año: {{ movie.anio }}</p>
        <p>Género: {{ Array.isArray(movie.generos) && movie.generos.length > 0 ? movie.generos.join(', ') : 'No disponible' }}</p>
        <p>Director: {{ movie.director }}</p>
        <div v-if="imagenCargada">
            <img :src="movie.portada" alt="Portada" @error="imagenCargada = false" style="max-width: 200px;" />
        </div>
        <p v-else class="no-portada">PORTADA NO DISPONIBLE</p>
        <p>Likes: {{ movie.likes }}</p>
        <button  @click="meGusta" :class="['botonMeGusta', { activo: likeActivo }]">👍 Me Gusta</button>
    </div>
</template>


<script setup lang="ts">
import { Pelicula } from '../interfaces/Pelicula'
import { ref } from 'vue'


//aqui cardComponent recibe del padre una prop movie con la estructura de pelicula
const props = defineProps<{
  movie: Pelicula
}>()


// aca se realiza un evento llama me_gusta , que cardComponente envio al padre, pasandole un id como dato
const emit = defineEmits<{
  (e: 'me_gusta', id: number): void
}>()


//es una CONSTANTE REACTIVA , inicia como true pero puede cambiar con @error="imagenCargada 
// en v-else>PORTADA NO DISPONIBLE
const imagenCargada = ref(true)

//es una constante reactiva, que da por sentado que no hay un me gusta en el boton
const likeActivo = ref(false)


//se realiza una funcion, que emplea un emit para avisarle al padre el id al cual se le dio click en me gusta
// luego cambia de estado const likeActivo de manera local
function meGusta() {
  emit('me_gusta', props.movie.id)
  likeActivo.value = !likeActivo.value
}
</script>

<style scoped>


.card {
  .card {
  background: rgba(255, 255, 255, 0.05); /* fondo semi-transparente */
  backdrop-filter: blur(10px); /* efecto vidrio */
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 30px;
  margin: 30px auto;
  width: 100%;
  max-width: 400px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.5);
  color: #ffffff;
}
}

.card h2 {
  margin-bottom: 10px;
  font-size: 1.6rem;
}

.card p {
  margin: 5px 0;
  font-size: 1rem;
}

.card img {
  display: block;
  margin: 15px auto;
  max-width: 200px;
  border-radius: 10px;
  border: 2px solid #00000033;
}

.botonMeGusta {
  background-color: #c3c3c3;
  color: black;
  padding: 10px 20px;
  margin-top: 10px;
  border: none;
  border-radius: 8px;
  font-weight: bold;
  transition: background-color 0.3s ease, transform 0.2s;
}

.botonMeGusta:hover {
  background-color: #999;
  transform: scale(1.05);
}

.botonMeGusta.activo {
  background-color: #2a2de6;
  color: white;
}

.no-portada {
  color: #ff4d4d; /* rojo suave */
  font-weight: bold;
  text-align: center;
  padding: 10px;
  background-color: rgba(255, 0, 0, 0.1);
  border-radius: 8px;
}
</style>