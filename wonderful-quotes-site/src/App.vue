<template>
  <div id="app" class="m-4">
    <app-header :maxQuotes="maxQuotes"></app-header>
    <quote-form @quoteAdded="newQuote"></quote-form>

    <div id="quotesContainer" class="container px-3">
      <div v-for="(quote, key) in quotes" :key="key" @click.prevent="deleteQuote(key)" class="d-inline-block rounded border m-2 p-3 quote-item">
        <h2>{{ quote }}</h2>
      </div>
    </div>

    <div class="container text-center px-4">
      <div class="alert alert-info">Info: Click on a Quote to delete it.</div>
    </div>

  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Quote from "./components/QuoteForm.vue";
export default {
  name: 'app',
  data () {
    return {
      quotes: [],
      maxQuotes: 0
    }
  },
  methods: {
    newQuote(quote) {
      this.quotes.push(quote);
      if(this.maxQuotes >= 10) {
        return alert("You've run out of space. Delete some quotes to add more.");
      } else {
        return this.maxQuotes++;
      }
    },
    deleteQuote(key) {
      this.$delete(this.quotes, key);
      console.log("deleted!");
      this.maxQuotes--;
    }
  },
  components: {
    'app-header': Header,
    'quote-form': Quote
  }
}

</script>

<style>

.form-control {
  height: 100px;
}

#quotesContainer {
  font-family: "Arizonia";
}

.quote-item:hover {
  background:#ffdddd;
}
</style>
