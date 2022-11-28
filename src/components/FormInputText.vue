<template>
<div class="mt-1 sm:mt-0 sm:col-span-2 max-w-lg">
    <input
        :id="name"
        :name="name"
        :type="type"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        v-bind="$attrs"
        class="
            shadow-sm
            focus:ring-primary
            focus:border-primary
            block
            w-full
            sm:text-sm
            border-gray-300
            rounded-md
        "
    />
</div>
</template>
<script>
export default {
  emits: ['update:modelValue'],
    props: {
        modelValue: {
            type: String,
        },
        name: {
            type: String,
        },
      type: {
          type: String,
        default: 'text'
      }
    },
};
</script>
