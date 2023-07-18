<template>
  <div>
    <h1>Contanos qué películas te gustaría ver</h1>
    <form v-bind:class="mostrarError ? 'error-form' : 'my-form'" @submit.prevent="agregarPelicula">
      <input type="text" v-model="nuevaPelicula" placeholder="Inserte su película" />
      <select v-model="tipoPelicula">
        <option value="2D">2D</option>
        <option value="3D">3D</option>
      </select>
      <button v-bind:class="mostrarError ? 'error-button' : 'my-button'" type="submit">Cargar</button>
    </form>

    <ul v-if="Array.isArray(peliculas) && peliculas.length > 0">
  <li v-for="(pelicula, index) in peliculas" :key="index">
    {{ pelicula.titulo }} - {{ pelicula.tipo }}
    <button @click="borrarPelicula(index)">Borrar</button>
  </li>
</ul>

    <p v-bind:class="mostrarError ? 'error-paragraph' : 'my-paragraph'" v-if="mostrarError">Por favor, complete los campos.</p>

   

    <contador :peliculas="peliculas" />
  </div>
</template>

<script>
import Contador from '@/components/ContadorComponente.vue';

export default {
  components: {
    Contador
  },
  data() {
    return {
      nuevaPelicula: '',
      tipoPelicula: '2D',
      peliculas: [],
      mostrarError: false
    };
  },
  mounted() {
    this.recuperarPeliculas();
  },
  methods: {
    agregarPelicula() {
      if (this.nuevaPelicula.trim() !== '' && this.tipoPelicula.trim() !== '') {
        const pelicula = {
          titulo: this.nuevaPelicula,
          tipo: this.tipoPelicula
        };
        this.peliculas.push(pelicula);
        this.nuevaPelicula = '';
        this.tipoPelicula = '';
        this.guardarPeliculas();
        this.mostrarError = false;
      } else {
        this.mostrarError = true;
      }
    },
    borrarPelicula(index) {
      if (confirm("Estas seguro desea eliminar: "  +this.peliculas[index].titulo + "?")) {
        this.peliculas.splice(index, 1);
      this.guardarPeliculas();
      } 
    
    },
    guardarPeliculas() {
      localStorage.setItem('peliculas', JSON.stringify(this.peliculas));
    },
    recuperarPeliculas() {
      const peliculas = localStorage.getItem('peliculas');
      console.log('Peliculas recuperadas:', peliculas);
      if (peliculas) {
        this.peliculas = JSON.parse(peliculas);
      }
    }
  }
};
</script>

<style>
.my-form {
  text-align: center;
  margin-top: 10px;
}

.error-form {
  text-align: center;
  margin-top: 10px;
  border: 2px solid red;
}

.my-button {
  background-color: rgb(156, 3, 3);
  color: white;
}

.error-button {
  background-color: red;
  color: white;
}

.my-paragraph {
  text-align: center;
}

.error-paragraph {
  text-align: center;
  color: red;
}

.my-form {
  text-align: center;
  margin-top: 10px;
}

.my-button {
  background-color: rgb(156, 3, 3);
  color: white;
}

.my-paragraph {
  text-align: center;
}

form {
  text-align: center;
  margin-top: 10px;
}

button {
  background-color: rgb(156, 3, 3);
  color: white;
}

html {
  background-color: rgb(216, 216, 221);
}

h2 {
  text-align: center;
}

li {
  list-style: none;
  text-align: center;
  margin-bottom: 10px;
}

button {
  background: #cf2121;
  background-image: -webkit-linear-gradient(top, #cf2121, #1f1f1f);
  background-image: -moz-linear-gradient(top, #cf2121, #1f1f1f);
  background-image: -ms-linear-gradient(top, #cf2121, #1f1f1f);
  background-image: -o-linear-gradient(top, #cf2121, #1f1f1f);
  background-image: linear-gradient(to bottom, #cf2121, #1f1f1f);
  -webkit-border-radius: 5;
  -moz-border-radius: 5;
  border-radius: 5px;
  font-family: Arial;
  color: #ffffff;
  font-size: 13px;
  padding: 5px 9px 7px 8px;
  text-decoration: none;
  margin-left: 10px;
}

p {
  text-align: center;
}

h1{
  text-align: center;
}
</style>
