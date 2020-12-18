<template>
    <h1>User Signup</h1>
    <p v-if="message">{{ message }}</p>
    <form v-else @submit.prevent="createUser">
        <label for="username">Username</label>
        <input required v-model="username" type="text" id="username" />

        <label for="password">Password</label>
        <input required v-model="password" type="text" id="password" />

        <label for="password-confirmation">Enter your password again</label>
        <input required v-model="confirmation" type="text" id="password-confirmation" />
        <p>{{ passwordsMatch ? "" : "Passwords gotta match" }}</p>

        <input type="submit" value="Create Account" />
    </form>
    <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    <ul>
      <li>Username: {{ username }}</li>
      <li>Password: {{ password }}</li>
      <li>Confirmation: {{ confirmation }}</li>
    </ul>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      username: "",
      password: "",
      confirmation: "",
      message: "",
      errorMessage: "",
    };
  },
  computed: {
    passwordsMatch() {
      return this.password === this.confirmation;
    },
  },
  methods: {
    createUser() {
      this.errorMessage = "";
      fetch("https://usersignup.com", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          username: this.username,
          password: this.password,
        }),
      }).then(response => response.json())
        .then(() => {
          this.message = "You're goin to Disneyland!";
        }).catch(() => {
          this.errorMessage = "Oops...";
        });
    },
  },
};
</script>

<style>
* {
    box-sizing: border-box;
}
form {
    max-width: 300px;
}
label, input {
    display: block;
}
input {
    margin-bottom: 16px;
    width: 100%;
}
input:valid {
  border-color: chartreuse;
}
input:invalid {
  border-color: red;
}
</style>
