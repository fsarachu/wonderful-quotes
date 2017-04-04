<template>
    <div v-if="quotes.length" class="content">
        <app-quote v-for="quote in quotes" :key="quote.id" @remove="removeQuote(quote)">{{ quote }}</app-quote>
    </div>
</template>

<script>
    import {bus} from '../main';
    import AppQuote from './Quote.vue';

    export default {
        components: {
            AppQuote
        },
        props: {
            quotes: {
                type: Array,
                required: true
            }
        },
        methods: {
            removeQuote(quote) {
                bus.$emit('quoteDeleted', quote);
            }
        }
    }
</script>