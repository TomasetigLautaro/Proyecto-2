<template>
 
  <div class="pelis">
    <h1>Peliculas en cartelera</h1>
    
    <img v-if="pelicula" :src="pelicula.Poster" :alt="pelicula.Title" class="poster" />
    <p>{{ pelicula.Title }}</p>
     

    <valoracion-pelicula />
    <img v-bind:src="spiderman" alt="Poster promocional de Spiderman"  />
   
    <img v-bind:src="transformers" alt="Poster promocional de Transformers" />
    <img v-bind:src="indiana" alt="Poster promocional de Indiana Jones" />
    <img v-bind:src="krakens" alt="Poster promocional de Krakens y Sirenas" />
    <img v-bind:src="rapidos" alt="Poster promocional de Rapidos y furiosos" />
    <img v-bind:src="barbie" alt="Poster promocional de Barbie" />
    <img v-bind:src="elementos" alt="Poster promocional de Elementos" />
    <img v-bind:src="flash" alt="Poster promocional de Flash" />
    <img v-bind:src="sirenita" alt="Poster promocional de La Sirenita" />
    <img v-bind:src="mision" alt="Poster promocional de Mision Imposible" />
   
  </div>
 
</template>

<script>
import ValoracionPelicula from '@/components/ValoracionPelicula.vue';
export default {
  components: {
    ValoracionPelicula
  },
  mounted(){
      fetch("https://www.omdbapi.com/?i=tt3896198&apikey=d1355d4a")
          .then(response => response.json())
          .then(response => {
            this.pelicula = response;
            console.log(response)
          localStorage.setItem("dato",JSON.stringify(this.pelicula))
          })
          .catch( err => console.error(err));



  },
  data() {
    return {
      pelicula: [],
      spiderman: require('@/assets/spiderman.jpg'),
      transformers: require('@/assets/transformers.jpg'),
      indiana: require('@/assets/indiana.jpg'),
      krakens: require('@/assets/krakens.jpg'),
      rapidos: require('@/assets/rapidos.jpg'),
      barbie: require('@/assets/barbie.jpg'),
      elementos: require('@/assets/elementos.jpg'),
      flash: require('@/assets/flash.jpg'),
      sirenita: require('@/assets/sirenita.jpg'),
      mision: require('@/assets/mision.jpg')
    };
  }
};
</script>

<style>
  img{
    margin-right: 50px;
    margin-top: 30px;
   
  }

  .pelis{
    text-align: center;
  }

  p{
    text-align: center;
  }

  .poster{
    text-align: center;
  }

  h1{
    text-align: center;
  }
  

</style>

