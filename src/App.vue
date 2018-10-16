<template>
    <div class="container">
        <!--ToDo: Use the Header component selector-->
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
            <!--Bind data props quoteCount and set it equal to the quote length-->
            <!--Bind data props maxQuotes and set it equal to the maxQuotes created below-->


        <!--ToDo: Use the NewQuote component selector-->
        <app-new-quote @quoteAdded="newQuote">

        </app-new-quote>
            <!--Initiate an $emit event listener called quoteAdded that is equal to newQuote-->

        <!--ToDo: Use the QuoteGrid component selector-->
        <app-quote-grid :quotes = "quotes" @quoteDeleted = "deleteQuote"></app-quote-grid>
            <!--Bind data props quotes and set it equal to the quotes array created below-->
            <!--Call quoteDeleted that is emitted from the QuoteGrid Component and pass the deleteQuote method created below-->
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
//  Todo: Import QuoteGrid, NewQuote, and Header Components
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';

    export default {
        data: function () {
            return {
                // ToDo: Create an array data object called quotes
                    // Have at least one string quote by default
                quotes: ["Time for a nap"],

                // ToDo: Create a data object maxQuotes that is set to 10
                maxQuotes:10
            }
        },
        methods: {
            // ToDo: Create a method that checks when a newQuote is created and takes the parameter quote.
                // This method will check if the quotes (Array Data Object) length is greater than or equal to the max quotes allowed
                // If it is return an alert telling the user to delete a quote
                // Outside of conditional, push quote (method parameter) to the quotes array
            newQuote(quote){
                if (this.quotes.length >= this.maxQuotes){
                    return alert('please delete quote first')
                }
                this.quotes.push(quote)
            },
            // ToDo: Create a method deleteQuote that takes in a parameter of index
                // This method will splice the quotes array by (index, 1)
            deleteQuote(index){
                this.quotes.splice(index, 1)
            }
        },
        components: {
            // ToDo: Initiate the QuoteGrid, NewQuote, and Header Components with Custom Selectors
            'app-quote-grid': QuoteGrid,
            'app-new-quote': NewQuote,
            'app-header': Header,
        }
        
    }
</script>

<style>
</style>
