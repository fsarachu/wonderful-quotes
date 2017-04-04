<template>
    <div>
        <div class="field">
            <label class="label">Add your quote:</label>
            <p class="control">
                <textarea v-model="quote" ref="textarea" class="textarea" placeholder="Some inspiring quote..."
                          autofocus></textarea>
            </p>
        </div>
        <div class="field is-grouped">
            <p class="control">
                <button type="submit" @click="addQuote" class="button is-primary">Add Quote</button>
            </p>
            <p class="control">
                <button @click="clearQuote" class="button is-link">Cancel</button>
            </p>
        </div>
    </div>
</template>

<script>
    import {bus} from '../main';

    export default {
        data: function () {
            return {
                quote: ''
            };
        },
        methods: {
            addQuote() {
                bus.$emit('addQuote', this.quote);
            },
            clearQuote() {
                this.quote = '';
            }
        },
        mounted() {
            bus.$on('quoteAdded', () => {
                this.clearQuote();
                this.$refs.textarea.focus();
            });
        }
    };
</script>

<style>
    .textarea {
        min-height: 3em;
    }
</style>