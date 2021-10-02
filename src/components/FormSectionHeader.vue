<template>
    <div>
        <h3 class="text-lg leading-6 font-medium text-gray-900">{{ title }}</h3>
        <p class="mt-1 max-w-2xl text-sm text-gray-500">
            <slot />
        </p>
    </div>
</template>

<script>
export default {
    props: {
       title: {
           type: String,
           required: true,
       }
    }
}
</script>
