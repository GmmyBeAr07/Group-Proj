<template>
<section id="Register" style="min-height: 88.6vh; min-width: 100vh; justify-content: center; flex-direction: column; display: flex;">

  <form @submit.prevent="register" class="form neu-border">
    <h2 class="form-heading">Register</h2>
    <input
      class="form-input neu-border-inset"
      type="text"
      v-model="name"
      placeholder="Name"
      required/>

    <input
      class="form-input neu-border-inset"
      type="email"
      v-model="email"
      placeholder="Email"
      required/>

    <input
      class="form-input neu-border-inset"
      type="text"
      v-model="contact"
      placeholder="Contact Number"
      required/>

    <input
      class="form-input neu-border-inset"
      type="password"
      v-model="password"
      placeholder="Password"
      required/>

    <button type="submit" class="form-btn neu-border">Sign up</button>
    <!-- <div class="form-social-login">
      <button class="form-btn neu-border form-social-btn">
        <i class="fab fa-google"></i>
      </button>
      <button class="form-btn neu-border form-social-btn">
        <i class="fab fa-facebook-f"></i>
      </button>
    </div> -->

    <p>
      Already a member?
      <router-link :to="{ name: 'Login' }">Sign in</router-link>
    </p>
  </form>
</section>
</template>


<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      contact: "",
      password: "",
    };
  },
  methods: {
    register() {
      fetch("https://generic-blog-api.herokuapp.com/users", {
        method: "POST",
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          contact: this.contact,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("User registered");
          localStorage.setItem("jwt", json.jwt);
          this.$router.push({ name: "Blogs" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>


<style>
#Register {
    background:linear-gradient(0deg, rgba(0, 0, 0, 0.555), rgba(0, 0, 0, 0.74)), url('../images/www2.jpg'); 
    background-repeat: no-repeat;
    background-attachment: fixed; 
    backface-visibility:visible;
    background-size: 100% 100%;
  }

.neu-border {
  border-radius: 30px;
  background: #f5f5f55e;
  box-shadow: 8px 8px 15px #66ff00, -8px -8px 15px #ffffff9f;
}
.neu-border-inset {
  border-radius: 30px;
  background: #f5f5f55e;
  box-shadow: 8px 8px 15px #66ff00, -8px -8px 15px #ffffff9f;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 40px;
  gap: 20px;
  width: 100%;
  max-width: 600px;
  margin-inline: auto;
}

.form-heading {
  text-align: center;
  text-transform: uppercase;
}

.form-input,
.form-btn {
  border: none;
  outline: none;
  padding: 20px;
}

.form-btn {
  cursor: pointer;
  transition: all 0.1s linear;
}

.form-btn:hover {
  transform: scale(1.05);
}

.form-social-login {
  display: flex;
  justify-content: space-between;
}

.form-social-btn {
  width: 45%;
  color: #333;
}
</style>
