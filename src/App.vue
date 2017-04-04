<template>
    <div id="app">
        <app-progress :current="quoteCount" :max="maxQuotes"></app-progress>
        <hr>
        <app-add-quote></app-add-quote>
    </div>
</template>

<script>
    import {bus} from './main';
    import AppProgress from './components/Progress.vue';
    import AppAddQuote from './components/AddQuote.vue';

    export default {
        components: {
            AppProgress,
            AppAddQuote
        },
        data: function () {
            return {
                quotes: [],
                maxQuotes: 10
            }
        },
        methods: {
            addQuote(quote) {
                if (this.quotes.length < this.maxQuotes) {
                    this.quotes.push(quote);
                }
            }
        },
        computed: {
            quoteCount() {
                return this.quotes.length;
            }
        },
        mounted() {
            bus.$on('quoteAdded', this.addQuote);
        }
    }
</script>

<style lang="sass">
    @import '../node_modules/bulma/bulma'
</style>
