<template>
  <div class="grid grid-cols-4 my-5">
    <label :for="'data' + name" class="p-2 text-right">{{ name }}</label>

    <input
      :id="'data' + name"
      :type="type"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      class="col-span-3 border border-gray-200 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent rounded-sm shadow-sm p-2 mx-3"
    />
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, reactive } from "vue";
export default defineComponent({
  name: "textInput",
  emits: ["update:modelValue"],
  props: {
    name: String,
    modelValue: String,
    type: { default: "text" },
  },
});
</script>

<style scoped>
</style>
