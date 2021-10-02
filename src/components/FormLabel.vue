
<template>
    <label
        class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2 sm:col-span-1"
        v-bind="$attrs"
        :class="$attrs.for ? 'cursor-pointer' : null"
    >
        <slot />
    </label>
</template>
