<template>
    <div id="app">
        <app-progress :current="quoteCount" :max="maxQuotes"></app-progress>
        <hr>
        <app-add-quote></app-add-quote>
        <hr>
        <app-quotes :quotes="quotes"></app-quotes>
    </div>
</template>

<script>
    import {bus} from './main';
    import AppProgress from './components/Progress.vue';
    import AppAddQuote from './components/AddQuote.vue';
    import AppQuotes from './components/Quotes.vue';

    export default {
        components: {
            AppProgress,
            AppAddQuote,
            AppQuotes
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
            },
            deleteQuote(quote){
                this.quotes.splice(this.quotes.indexOf(quote), 1);
            }
        },
        computed: {
            quoteCount() {
                return this.quotes.length;
            }
        },
        mounted() {
            bus.$on('quoteAdded', this.addQuote);
            bus.$on('quoteDeleted', this.deleteQuote);
        }
    }
</script>

<style lang="sass">
    @import '../node_modules/bulma/bulma'

    #app
        max-width: 500px
        padding: 2rem 1rem
        margin: 0 auto
</style>
