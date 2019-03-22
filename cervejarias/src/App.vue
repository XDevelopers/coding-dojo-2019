<template>
  <div id="app">
    <nav-bar />
    <div class="page-content">
      <router-view/>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from '@/components/NavBar';
export default {
  name: 'App',
  data() {
    return {      
    }
  },
  // Components
  components: {
    NavBar,
  },
} 
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
#nav {
  
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
