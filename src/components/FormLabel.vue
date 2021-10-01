
<template>
    <label
        class="block text-sm font-medium text-gray-700"
        v-bind="$attrs"
        :class="$attrs.for ? 'cursor-pointer' : null"
    >
        <slot />
    </label>
</template>
