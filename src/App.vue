<template>
  <div class="weather" :class="weatherClass">
    <div class="container">
      <div class="card weather-form">
        <input type="text" class="weather-form__input" v-model="searchQuery" @keyup.enter="weatherSearch" placeholder="Enter city">
        <button class="weather-form__btn" @click="weatherSearch">Search</button>
      </div>
      <div class="card weather-loading" v-if="loading">Loading...</div>
      <div class="weather-info" v-show="!error && location && temp !== 0 && descr">
        <div class="card" v-if="error">Error!!</div>
        <div class="weather-info__text">
          <p class="card">{{ location }}</p>
          <p class="card">{{ temp }}°C</p>
          <p class="card">{{ descr }}</p>
        </div>
      </div>
    </div>
    <div class="weather-bg">
      <div>
        <img class="weather-bg__img bg" src="./images/standard.jpg" alt="">
        <img class="weather-bg__img clear" src="./images/clear-sky.jpg" alt="clear">
        <img class="weather-bg__img few" src="./images/few-clouds.jpg" alt="few clouds">
        <img class="weather-bg__img scattered" src="./images/scattered-clouds.jpg" alt="scattered clouds">
        <img class="weather-bg__img overcast" src="./images/overcast.jpg" alt="overcast clouds">
        <img class="weather-bg__img broken" src="./images/broken-clouds.jpg" alt="broken clouds">
        <img class="weather-bg__img heavy" src="./images/shower-rain.jpg" alt="">
        <img class="weather-bg__img moderate" src="./images/moderate.jpg" alt="">
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
    return {
      location: '',
      temp: '',
      descr: '',
      loading: false,
      error: false,
      searchQuery: '',
     }
  },
    computed: {
      weatherClass() {
        const desc = this.descr.toLowerCase();
    switch (true) {
    case desc.includes('clear'):
      return 'clear';
    case desc.includes('few clouds'):
      return 'few';
    case desc.includes('scattered clouds'):
      return 'scattered';
    case desc.includes('overcast clouds'):
      return 'overcast';
    case desc.includes('broken clouds'):
      return 'broken';
      case desc.includes('moderate rain'):
      return 'moderate';
    case desc.includes('heavy rain'):
      return 'heavy';
    case desc.includes('rain'):
      return 'rain';
      case desc.includes('drizzle'):
      return 'rain';
    case desc.includes('thunderstorm'):
      return 'thunderstorm';
    case desc.includes('snow'):
      return 'snow';
    case desc.includes('mist'):
      return 'mist';
    default:
      return '';
  }
}
    },
    methods: {
      weatherSearch() {
        this.loading = true;
        this.error = false;
        fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.searchQuery}&appid=8ffe6449c5da40e64905d7a9f8d0ee6e&units=metric`).then(response => response.json()).then(data => {
          console.log(data);
          this.loading = false;
          this.location = data.name;
          this.temp = data.main.temp;
          this.descr = data.weather[0].description;
          this.resetSearchQuery()
        }).catch(error => {
          this.loading = false;
          this.error = true;
          console.error(error);
         })
      },
      resetSearchQuery() {
        this.searchQuery = ''
      }
    }
  }
</script>