<template>
  <div id="app">
    <Header :current="current" />
    <Body
      :forecast="forecast"
      :paris="paris"
      :lyon="lyon"
    />
  </div>
</template>

<script>
import Header from './components/header/Header';
import Body from './components/body/Body';
export default {
  name: 'App',
  components: {
    Header,
    Body
  },
  data() {
    return {
      current: {},
      forecast: [],
      paris: {},
      lyon: {}
    }
  },
  created() {
    const localWeather = () => {
      const APIKEY = "acbe571709d34e4160a6ece108b21586";
      // Este trae el del dia presente y 7 dias en adelante
      const url = `https://api.openweathermap.org/data/2.5/onecall?lat=4.60971&lon=-74.08175&exclude=minutely,hourly,&appid=${APIKEY}`;
      this.$http.get(url)
        .then((res) => {
          this.current = res.body.current;
          this.current.weather = res.body.current.weather[0];
          this.forecast = res.body.daily.slice(1,4)
        });
    }
    localWeather();

    const InternationalWeather = (ciudad) => {
      const APIKEY = "acbe571709d34e4160a6ece108b21586";
      // Este trae el del dia presente y 7 dias en adelante
      const url = `https://api.openweathermap.org/data/2.5/weather?q=${ciudad}&appid=${APIKEY}`;
      let data = {}
      this.$http.get(url)
        .then((res) => {
          this[ciudad] = res.body;
          this[ciudad].weather = res.body.weather[0];
        });
    }
    InternationalWeather('paris');
    InternationalWeather('lyon');
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  #app {
    font-family: 'Montserrat', sans-serif;
  }
</style>
