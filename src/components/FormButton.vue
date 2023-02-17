<template>
  <button class="button" :disabled="disabled">{{ text }}</button>
</template>
  
  
  <script>
export default {
  props: {
    text: {
      type: String,
      required: true,
    },
    disabled: {
      type: Boolean,
      required: false,
    },
  },
};
</script>
  
  
  <style scoped>
.button {
  display: block;
  padding: 7px 12px;
  background-color: aqua;
  border-radius: 7px;
  font-weight: bold;
  font-size: 15px;
  width: 100%;
  border: none;
  margin-top: 10px;
  cursor: pointer;
}
.button:hover {
  opacity: 0.7;
}
.button:disabled {
  opacity: 0.4;
}
</style>