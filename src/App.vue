<template>
  <div id="app">
   
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      data: {}
    }
  },
  beforeCreate() {
    const consultAPI = () => {
      const APIKEY = "acbe571709d34e4160a6ece108b21586";
      // const url = `http://api.openweathermap.org/data/2.5/weather?q=bogota,colombia&appid=${APIKEY}`;
      // Este trae el del dia presente y 7 dias en adelante
      const url = `https://api.openweathermap.org/data/2.5/onecall?lat=4.60971&lon=-74.08175&exclude=minutely,hourly,&appid=${APIKEY}`;

      let req =  new XMLHttpRequest();
      req.open("GET", url, true);
      
        console.log(req);
      req.onreadystatechange = () => {
        req.status === 200 ? this.data = req.response  : console.log('Error');
      }
      req.send(null);
    }
    consultAPI();
  },
  computed: {
    formatData() {
      return JSON.parse(this.data)
    }
    
  }
  
}
</script>

<style lang="scss">
#app {
  
}
</style>
