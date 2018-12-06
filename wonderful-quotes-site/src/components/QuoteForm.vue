<template>
  <div class="container mb-5">
    <div class="row">
      <div class="col">
        <div id="quoteForm">
          <p>Quote</p>
          <textarea type="text" v-model="quote" class="form-control mb-1"></textarea>
          <button class="btn btn-primary text-white p-1" type="submit" @click.prevent="createQuote">Add Quote</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data: function() {
      return {
        quote: ""
      }
    },
    methods: {
      createQuote() {
        this.$emit("quoteAdded", this.quote);
        this.quote = "";
      }
    }
  }
</script>

<style>
#quoteForm {
  width:60%;
  margin:auto;
}
</style>
