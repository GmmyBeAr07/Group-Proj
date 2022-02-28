<template>
  <section id="Home" style="min-height: 100vh; justify-content: center; flex-direction: column; display: flex;">
        
        <div class="w3-container w3-center w3-animate-top">
<span class="h1"><h1>Welcome To </h1></span>
<span class="h2"><h2>Hire Your Own Developer</h2></span>
<br>
<span class="h3"><h3><button>Hire Us</button></h3></span>
</div> 
  </section>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>


<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
