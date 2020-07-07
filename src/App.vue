<template>
  <div class="container">
    <app-progress-bar :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-progress-bar>
    <app-new-quote @quoteAdded="addQuote"></app-new-quote>
    <app-quote-grid :quotes='quotes' @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Click on a quote to delete it.</div>
      </div>
    </div>
  </div>
</template>

<script>
  import ProgressBar from './components/ProgressBar.vue'
  import QuoteGrid from './components/QuoteGrid.vue'
  import NewQuote from './components/NewQuote.vue'

  export default {
    data(){
      return {
        quotes: [
          'test quote'
          ],
        maxQuotes: 10
      }
    },
    methods: {
      addQuote(event){
        if (this.quotes.length >= this.maxQuotes) {
          return alert('Error:  Max size reached! Delete quotes before adding more.')
        }
        this.quotes.push(event)
      },
      deleteQuote(event){
        this.quotes.splice(event, 1)
      }
    },
    components: {
      appQuoteGrid: QuoteGrid,
      appNewQuote: NewQuote,
      appProgressBar: ProgressBar
    }
  }

</script>

<style>
</style>
