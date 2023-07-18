<template>
    <div>
      <h2>Películas cargadas: {{ contador() }}</h2>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      peliculas: {
        type: Array,
        required: true
      }
    },
    methods: {
      contador() {
        return this.peliculas.length;
      }
    }
  };
  </script>
  