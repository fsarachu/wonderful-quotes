<template>
    <div>
        <h3 class="title is-4 has-text-centered">Quotes added: {{ current }} / {{ max }}</h3>
        <progress class="progress is-primary" :value="current" :max="max"></progress>
    </div>
</template>

<script>
    export default {
        props: {
            max: {
                type: Number,
                required: true
            },
            current: {
                type: Number,
                required: true
            }
        }
    };
</script>

<style>
    progress[value]::-webkit-progress-value {
        transition: all .3s ease-out;
    }
</style>