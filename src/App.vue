<template>
  <!-- <div class="weather"></div> -->
</template>

<script>
export default {
  data() {
    this.weaterSearch()
    return {

      }
  },
    // computed: {

    // }
    methods: {
    weaterSearch() {
        fetch("https://api.openweathermap.org/data/2.5/weather?q=milan&appid=8ffe6449c5da40e64905d7a9f8d0ee6e&units=metric").then(response => response.json()).then(data => console.log(data))
      },
      // resetSearchQuery() {

      // }
    }
  }
</script>