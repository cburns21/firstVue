<template>
    <div>
        <appHeader />
        <quote v-for="(quote, i) in quotes"  v-bind:ronQuote='quote' v-bind:key='"ron" + i'/>
        <button v-on:click="getQuotes" class="btn btn-warning">Get Swanson</button>
    </div>
</template>

<script>
import appHeader from '../components/appHeader.vue'
import quote from '../components/quote.vue'
import getButton from '../components/getButton.vue'
export default {
    data() {
        return {
            quotes: ''
        }
    },
    components: {
        appHeader,
        quote,
        getButton
    },
    methods: {
        getQuotes(){
            fetch('https://ron-swanson-quotes.herokuapp.com/v2/quotes/2')
            .then(resp => resp.json())
            .then(resp => this.quotes = resp)
        }
    },
    mounted() {
        this.getQuotes()
    }
}
</script>

<style scoped>

</style>
