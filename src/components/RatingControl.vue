<template>
  <ul>
    <!-- giving a type: button property prevents it from submitting the form -->
    <!-- binding the active class if the button is selected -->
    <li value="poor" :class="{active: modelValue === 'poor'}">
      <button type="button" @click="activate('poor')">Poor</button>
    </li>
    <li value="average" :class="{active: modelValue === 'average'}">
      <button type="button" @click="activate('average')">Average</button>
    </li>
    <li value="great" :class="{active: modelValue === 'great'}">
      <button type="button" @click="activate('great')">Great</button>
    </li>
  </ul>
</template>

<script>
export default {
  // the props and emit value are decided by vue in this instance
  props: ['modelValue'],
  emits: ['update:modelValue'],
  methods: {
    // using the activeOption to send the option selected with v-model to TheForm.vue
    activate(option) {
      this.$emit('update:modelValue', option)
    }
  }
}
</script>

<style scoped>
.active, .active button {
  background-color: teal;
  color: white;
}

ul {
  list-style-type: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  padding: 1rem;
  border: 1px solid #ccc;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>