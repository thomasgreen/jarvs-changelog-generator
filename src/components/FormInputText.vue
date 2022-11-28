<template>
  <div class="mt-1 sm:mt-0 sm:col-span-2 max-w-lg">
    <input
      :id="name"
      :name="name"
      :type="type"
      :value="modelValue"
      v-bind="$attrs"
      class="shadow-sm focus:ring-primary focus:border-primary block w-full sm:text-sm border-gray-300 rounded-md"
      @input="$emit('update:modelValue', $event.target.value)"
    >
  </div>
</template>

<script>
export default {
  props: {
    modelValue: {
      type: String,
    },
    name: {
      type: String,
    },
    type: {
      type: String,
      default: "text",
    },
  },
  emits: ["update:modelValue"],
};
</script>
