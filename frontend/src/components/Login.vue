<template>
  <div class="login">
    <div>
      <form @submit.prevent="submit">
        <div>
          <label for="email">E-mail</label>
          <input type="email" name="email" v-model="form.email" />
        </div>
        <div>
          <label for="password">Password</label>
          <input type="password" name="password" v-model="form.password" minlength="8" />
        </div>
        <button type="submit">Login</button>
      </form>
    </div>
    <p v-if="showError" id="error">Wrong e-mail or password</p>
  </div>
</template>

<script>
import { mapActions } from "vuex";
import store from "../store";
export default {
  name: "Login",
  components: {},
  data() {
    return {
      form: {
        email: "",
        password: "",
      },
      showError: false
    };
  },
  methods: {
    ...mapActions(["LogIn"]),
    async submit() {
      try {
        await this.LogIn(this.form);
        this.$router.push("/");
      } catch (error) {
        console.log(error);
      }
      if (!store.getters.isAuthenticated) {
      this.showError = true;
      }
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
label {
  padding: 12px 12px 12px 0;
  display: inline-block;
}
button[type="submit"] {
  background-color: #4caf50;
  color: white;
  padding: 12px 20px;
  cursor: pointer;
  border-radius: 30px;
}
button[type="submit"]:hover {
  background-color: #45a049;
}
input {
  margin: 5px;
  box-shadow: 0 0 15px 4px rgba(0, 0, 0, 0.06);
  padding: 10px;
  border-radius: 30px;
}
#error {
  color: red;
}
</style>