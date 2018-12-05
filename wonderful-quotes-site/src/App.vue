<template>
  <div id="app">

    <div class="container my-4 px-4">
      <h1>Quotes Added</h1>
      <div class="rounded border w-100">
        <div class="bg-primary text-white text-center" :style="{width: maxQuotes + '0%'}"> {{ maxQuotes}}/10</div>
      </div>
    </div>

    <div class="container mb-5">
      <div class="row">
        <div class="col">
            <div id="quoteForm">
              <p>Quote</p>
              <input type="text" id="clientInput" class="form-control mb-1" />
              <button class="btn btn-primary text-white p-1" type="submit" @click="renderQuote">Add Quote</button>
            </div>
        </div>
      </div>
    </div>

    <div id="quotesContainer" class="container px-3">
      <div v-for="(quote, key) in quotes" :key="key" @click="deleteQuote(key)" class="d-inline-block rounded border m-2 p-3">
        <h2>{{ quote }}</h2>
      </div>
    </div>

    <div class="bg-info p-2 text-center fixed-bottom">Info: Click on a Quote to delete it.</div>

  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      quotes: [],
      maxQuotes: 0,
    }
  },
  methods: {
    renderQuote: function() {
      var quoteInput = document.getElementById("clientInput").value;
      this.quotes.push(quoteInput);

      if(this.maxQuotes >= 10) {
        alert("You've run out of space. Delete some quotes to add more.");
      } else {
        this.maxQuotes++;
      }
    },
    deleteQuote: function(key) {
      this.$delete(this.quotes, key);
      console.log("deleted!");
      this.maxQuotes--;
    }
  }
}
</script>

<style>
.quoteBar {
  height:20px;
  width: 0%;
}

#quoteForm {
  width:60%;
  margin:auto;
}

.form-control {
  height: 100px;
}

#quotesContainer {
  font-family: "Arizonia";
}
</style>
