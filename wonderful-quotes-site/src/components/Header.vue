<template>
  <div class="container my-4 px-4">
    <h1>Quotes Added</h1>
    <div class="progress rounded border w-100">
      <div class="progress-bar bg-primary text-white text-center" :style="{width: maxQuotes + '0%'}"> {{ maxQuotes}}/10</div>
    </div>
  </div>

</template>

<script>
  export default {
    props: ["maxQuotes"]
  }
</script>
