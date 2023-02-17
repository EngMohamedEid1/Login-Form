<template>
  <div class="form-labels">
    <label class="form-label" :for="name">{{ name }}</label>
    <div class="form-error">{{ error }}</div>
  </div>
  <input @input="input" :type="type" :id="name" class="form-input" />
</template>


<script>
export default {
  emits: ["updateValue"],
  data() {
    return {};
  },
  props: {
    value: {
      required: true,
    },
    error: {
      type: String,
    },
    name: {
      type: String,
      required: true,
    },
    type: {
      type: String,
      default() {
        return "text";
      },
    },
    rules: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  methods: {
    input($e) {
      // console.log($e.target.value);
      this.$emit("updateValue", {
        value: $e.target.value,
        error: this.validate($e.target.value),
        name: this.name.toLowerCase(),
      });
    },
    validate(value) {
      if (this.rules.required && value.length === 0) {
        return "required";
      }
      if (this.rules.min && value.length < this.rules.min) {
        return `Min length is ${this.rules.min}`;
      }
    },
  },
};
</script>

<style scoped>
.form-labels {
  display: flex;
  justify-content: space-between;
}
.form-error {
  color: red;
}
.form-input {
  color: #000;
  padding: 5px;
  margin: 1rem 0.5rem;
  border: none;
  outline: none;
  border-radius: 7px;
}
</style>