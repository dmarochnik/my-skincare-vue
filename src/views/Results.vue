<template>
  <div id="results">
    <h1>{{test}}</h1>
  </div>
</template>

<script>
export default {
  name: "Results",
  data() {
    return {
      test: this.$attrs.results
    }
  }
}
</script>

<style scoped>

</style>