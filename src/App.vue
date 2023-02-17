<template>
  <form class="form" @submit="submit">
    <FormInput
      :rules="username.rules"
      :error="username.error"
      type="text"
      name="Username"
      @updateValue="update"
    ></FormInput>
    <FormInput
      :rules="password.rules"
      :error="password.error"
      :value="password.value"
      type="Password"
      name="Password"
      @updateValue="update"
    ></FormInput>
    <FormButton text="Login Now" :disabled="!isValid"></FormButton>
  </form>
</template>

<script>
import FormInput from "./components/FormInput.vue";
import FormButton from "./components/FormButton";
export default {
  name: "App",
  components: {
    FormInput,
    FormButton,
  },
  data() {
    return {
      username: {
        value: "",
        error: "",
        rules: {
          required: true,
          min: 4,
        },
      },
      password: {
        value: "",
        error: "",
        rules: {
          required: true,
          min: 8,
        },
      },
    };
  },
  methods: {
    update({ name, value, error }) {
      this[name].error = error;
      this[name].value = value;
    },
    submit($e) {
      $e.preventDefault();
      console.log({
        username: this.username.value,
        password: this.password.value,
      });
    },
  },
  computed: {
    isValid() {
      return !this.username.error && !this.password.error;
    },
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  flex-direction: column;
}

.form {
  padding: 2em;
  border-radius: 10px;
  background: linear-gradient(90deg, rgb(149, 215, 149), rgb(162, 93, 183));
}
</style>
