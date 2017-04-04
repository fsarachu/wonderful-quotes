<template>
    <blockquote>
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