<template>

<section id="Landing" style="min-height: 88.7vh; width: 100%; justify-content: center; flex-direction: column; display: flex;">

<div class="w3-container w3-center w3-animate-top">
<span class="h1"><h1>Welcome To...</h1></span>
<span class="h2"><h2>Artistic Albums</h2></span>

<br>

<a class="logiii" href="../login">Login</a>

<a class="signiii" href="../register">Sign Up</a>
</div> 
 </section>
</template>

<script>
export default {
  name: 'Landing',
  props: {
    msg: String
  }
}
</script>

<style scoped>
.landingbuttons {
  color: redq
}

#Landing {
    background:linear-gradient(0deg, rgba(0, 0, 0, 0.534), rgba(0, 0, 0, 0.733)), url('../images/guit.jpg'); 
    background-repeat: no-repeat;
    background-attachment: fixed; 
    backface-visibility:visible;
    background-size: 100% 100%;
  }


</style>
