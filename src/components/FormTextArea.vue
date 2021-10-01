<template>
    <div class="mt-1">
        <textarea
            :name="name"
            :required="required"
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)"
            rows="3"
            class="
                shadow-sm
                focus:ring-indigo-500
                focus:border-indigo-500
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
