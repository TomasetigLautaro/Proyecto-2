<template>
    <div class="valoracion-pelicula">
      <h2>Si has visto esta pelicula, contanos que te parecio!</h2>
      
      <div class="stars">
        <span
          v-for="(star, index) in 5"
          :key="index"
          :class="{ filled: index < rating }"
          @mouseover="hoverRating(index + 1)"
          @mouseout="hoverRating(0)"
          @click="setRating(index + 1)"
        >
          ★
        </span>
      </div>
      <p v-if="rating > 0">Has valorado la película con {{ rating }} estrellas.</p>
      <p v-else>Aún no has valorado la película.</p>
      
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        rating: 0,
        hoveredRating: 0
      };
    },
    methods: {
      setRating(rating) {
        this.rating = rating;
        
      },
      hoverRating(rating) {
        this.hoveredRating = rating;
      }
    }
  };
  </script>
  
  <style scoped>
  .valoracion-pelicula {
    text-align: center;
  }
  
  .stars {
    font-size: 24px;
    cursor: pointer;
  }
  
  .stars span {
    color: #ccc;
    transition: color 0.3s;
  }
  
  .stars span.filled {
    color: #ffbb00;
  }
  </style>
  