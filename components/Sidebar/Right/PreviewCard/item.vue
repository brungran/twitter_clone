<template>
    <div class="p-3 cursor-pointer border-b hover:bg-gray-100 dark:hover:bg-dim-300" :class="wrapperClasses">
        <slot />
    </div>
</template>

<script setup>
    const {defaultTransition, twitterBorderColor} = useTailwindConfig()
    const wrapperClasses = computed(() => `${defaultTransition} ${twitterBorderColor}`)
</script>