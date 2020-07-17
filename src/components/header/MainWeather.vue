<template>
  <div class="main-weather">
    <div class="weather">
      <img
        v-if="weather.icon"
        class="weather-icon"
        :src="require(`@/assets/icons/${ weather.icon }.png`)"
        alt="current weater icon"
      >
      <p v-if="weather.main" class="weather-text">{{ weather.main }}</p>  
    </div>
    <div class="degress">
      <p class="degress-text">{{ current.temp - 273.15 }}<sup>°c</sup></p>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainWeather",
  props: {
    current: Object
  },
  computed: {
    weather() {
      return this.current.weather ? this.current.weather : false
    }
  }
}
</script>

<style lang="scss">
  @import '../../_vars.scss';
  .main-weather {
    position: absolute;
    top: 50%;
    left: 0;
    transform: translateY(-50%);
    background: $purple-light;
    width: 7rem;
    height: 14rem;
    border-radius: 0 2rem 2rem 0;
    color: #fff;
    .weather {
      width: 100%;
      height: 55%;
      border-radius: 0 2rem 2rem 1rem;
      background: $purple-dark;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      .weather-icon {
        width: 50px;
        margin-bottom: 0.5rem;
      }
      .weather-text {
        font-size: 0.8rem;
      }
    }
    .degress {
      width: 100%;
      height: 45%;
      display: flex;
      justify-content: center;
      align-items: center;
      .degress-text {
        font-size: 3rem;
        font-weight: 500;
        sup {
          font-size: 1rem;
        }
      }
    }
  }
</style>