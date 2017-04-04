<template>
    <div id="app">
        <app-progress :current="quoteCount" :max="maxQuotes"></app-progress>
    </div>
</template>

<script>
    import AppProgress from './components/Progress.vue';

    export default {
        components: {
            AppProgress
        },
        data: function () {
            return {
                quotes: [],
                maxQuotes: 10
            }
        },
        computed: {
            quoteCount() {
                return this.quotes.length;
            }
        }
    }
</script>

<style lang="sass">
    @import '../node_modules/bulma/bulma'
</style>
