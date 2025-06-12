<template>
  <div class="weather">
    <div class="container">
      <div class="card weather-form">
        <input type="text" class="weater-form__input" placeholder="Enter city">
        <button class="weather-form__btn">Search</button>
      </div>
      <div class="card weather-loading">Loading...</div>
      <div class="weather-info">
        <div class="weather-info__text">
          <p class="card">Phuket</p>
          <p class="card">29°C</p>
          <p class="card">Sunny</p>
          <p class="card"></p>
        </div>
      </div>
    </div>
    <div class="weather-bg">
      <div>
        <img class="weather-bg__img bg" src="./images/standard" alt="">
        <img class="weather-bg__img clear" src="./images/clear-sky.jpg" alt="clear">
        <img class="weather-bg__img few" src="./images/few-clouds.jpg" alt="few clouds">
        <img class="weather-bg__img scattered" src="./images/scattered-clouds.jpg" alt="scattered clouds">
        <img class="weather-bg__img broken" src="./images/broken-clouds.jpg" alt="broken-clouds">
        <img class="weather-bg__img shower" src="./images/shower-rain.jpg" alt="">
        <img class="weather-bg__img rain" src="./images/rain.jpg" alt="">
        <img class="weather-bg__img thunderstorm" src="./images/thunderstorm.jpg" alt="">
        <img class="weather-bg__img snow" src="./images/snow.jpg" alt="">
        <img class="weather-bg__img mist" src="./images/mist.jpg" alt="">
       </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    this.weatherSearch()
    return {

      }
  },
    // computed: {

    // }
    methods: {
    weatherSearch() {
        fetch("https://api.openweathermap.org/data/2.5/weather?q=milan&appid=8ffe6449c5da40e64905d7a9f8d0ee6e&units=metric").then(response => response.json()).then(data => console.log(data))
      },
      // resetSearchQuery() {

      // }
    }
  }
</script>