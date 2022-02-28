<template>

<section id="Login" style="min-height: 88.7vh; min-width: 100vh; justify-content: center; flex-direction: column; display: flex;">

  <form @submit.prevent="login" class="form neu-border">
    <h2 class="form-heading">Login</h2>
    <input
      class="form-input neu-border-inset"
      type="email"
      v-model="email"
      placeholder="Email"/>

    <input
      class="form-input neu-border-inset"
      type="password"
      v-model="password"
      placeholder="Password"/>

    <p>
      Not a member?
      <router-link :to="{ name: 'Register' }">Create an account</router-link>
    </p>
  </form>
</section>
</template>


<script>
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    login() {
      fetch("https://generic-blog-api.herokuapp.com/users", {
        method: "PATCH",
        body: JSON.stringify({
          email: this.email,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          localStorage.setItem("jwt", json.jwt);
          alert("User logged in");
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
#Login {
    background:linear-gradient(0deg, rgba(0, 0, 0, 0.555), rgba(0, 0, 0, 0.74)), url('../images/www.png'); 
    background-repeat: no-repeat;
    background-attachment: fixed; 
    backface-visibility:visible;
    background-size: 100% 100%;
  }

.neu-border {
  border-radius: 30px;
  background: #f5f5f55e;
  box-shadow: 8px 8px 15px #0f970a, -8px -8px 15px #ffffff8a;
}
.neu-border-inset {
  border-radius: 30px;
  background: #f5f5f55e;
  box-shadow: 8px 8px 15px #0f970a, -8px -8px 15px #ffffff8c;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: right;
  padding: 40px;
  gap: 20px;
  width: 50%;
  margin-inline: auto;
  max-width: 600px;
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
