<template>
    <blockquote @click="$emit('remove')">
        <slot></slot>
    </blockquote>
</template>

<script>
    export default {
        data: function () {
            return {
                isAlive: true
            };
        }
    }
</script>