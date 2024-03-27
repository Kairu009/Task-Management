<template>
  <div class="login-form">
    <h2>Welcome!</h2>
    <form @submit.prevent="login">
      <div class="form-group">
        <label for="username">Username:</label>
        <input
          type="text"
          id="username"
          placeholder="Enter your username"
          v-model="username"
          required
        />
      </div>
      <div class="form-group">
        <label for="password">Password:</label>
        <input
          type="password"
          id="password"
          placeholder="Enter your password"
          v-model="password"
          required
        />
      </div>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    login() {
      // check if the username and password match the default values
      if (this.username === "admin" && this.password === "admin") {
        // set the username and password in localStorage
        localStorage.setItem("username", this.username);
        localStorage.setItem("password", this.password);
        this.$router.push({ name: "task" });
      } else {
        alert("Invalid username or password");
      }
    },
  },
};
</script>

<style>
.login-form {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 5px;
}

h2 {
  text-align: center;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input[type="text"],
input[type="password"],
button {
  width: 100%;
  padding: 10px;
  font-size: 15px;
  background: #ffffff;
  border: 1px solid hsla(160, 100%, 37%, 1);
  border-radius: 5px;
  box-sizing: border-box; /* Include padding and border in the element's total width */
}

button {
  background-color: hsla(160, 100%, 37%, 1);
  color: #fff;
  font-weight: 600;
  cursor: pointer;
  margin-top: 10px; /* Add some space between input fields and the button */
}

@media screen and (max-width: 600px) {
  .login-form {
    max-width: 300px;
  }
}
</style>
