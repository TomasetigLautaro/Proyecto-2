<template>
  <div id="app">
    <nav>
      
      <router-link to="/">Feedback</router-link> |
      <router-link to="/cartelera">Cartelera</router-link> 
     
      
    </nav>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
 
  color: #00060c;
  
}

nav {
  padding: 30px;
  background-color: rgb(98, 98, 98);
}

nav a {
  font-weight: bold;
  color: #ffffff;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: rgb(156, 3, 3);
}
</style>
