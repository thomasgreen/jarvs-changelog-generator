<template>
    <div class="sm:col-span-6">
        <label :for="name" class="block text-sm font-medium text-gray-700">
            {{ label }}
        </label>
        <div class="mt-1">
            <textarea
                :id="name"
                :name="name"
                :required="required"
                v-model="formData.description"
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
    </div>
</template>

<script>
export default {
    props: {
        name: {
            type: String,
            required: true,
        },
        label: {
            type: String,
            required: true,
        },
    },
};
</script>
