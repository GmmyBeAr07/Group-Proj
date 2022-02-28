<template>
  <div class="home">
  
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>

<style scoped>
section {
    background:linear-gradient(0deg, rgba(0, 0, 0, 0.281), rgba(56, 10, 10, 0.877)), url('../assets/images/code.jpg');
    background-repeat: no-repeat;
    background-attachment: fixed; 
    backface-visibility:visible;
    background-size: 100% 100%;
  }

#form-control {
 min-width: 40%;
}
</style>
