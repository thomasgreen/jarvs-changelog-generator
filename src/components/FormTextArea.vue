<template>
    <div class="mt-1 sm:mt-0 sm:col-span-2 max-w-lg">
        <textarea
            :name="name"
            :required="required"
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)"
            rows="3"
            class="
                shadow-sm
                focus:ring-primary
                focus:border-primary
                block
                w-full
                sm:text-sm
                border border-gray-300
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
        required: {
            type: Boolean,
            default: false,
        },
    },
};
</script>
