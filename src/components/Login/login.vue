<template>
  <div class="container mx-auto max-w-xl shadow-2xl rounded-xl p-8 bg-blue-50">
    <h2>Create New Account</h2>
    <form @submit.prevent="submit()">
      <textInput :name="'User name'" v-model="logInInformation.username" />
      <textInput
        :type="'e-mail'"
        :name="'E-mail'"
        v-model="logInInformation.email"
      />
      <textInput
        :type="'password'"
        :name="'Password'"
        v-model="logInInformation.password"
      />
      {{ logInInformation.user }}
      <button
        type="submit"
        class="text-gray-100 bg-purple-300 hover:bg-purple-400 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:ring-opacity-90 rounded-md shadow-sm p-2 mx-3"
      >
        Sign up
      </button>
    </form>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent } from "vue";
import textInput from "./textInput.vue";
export default defineComponent({
  name: "LogIn",
  components: {
    textInput,
  },
  methods: {
    submit() {
      this.axios
        .post("http://localhost:8000/users/sign_up", this.logInInformation)
        .then((response) => console.log(response));

      console.log(this.logInInformation);
    },
  },
  setup: () => {
    const logInInformation = {
      username: "",
      email: "",
      password: "",
    };
    return { logInInformation };
  },
});
</script>

<style scoped>
</style>
