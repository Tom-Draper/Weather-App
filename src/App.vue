<template>
  <div id="app" :class="typeof weather.main != 'undefined' ? 'temp' + Math.round(weather.main.temp)  : ''">
    <main>
    <div class="top-bar">
      <div class="search-box">
        <input type="text" 
        class="search-bar" 
        placeholder="Search..."
        v-model="query"
        @keyup.enter="fetchWeather"
        />
      </div>
      <div class="location-box" v-if="typeof weather.main != 'undefined'">
        <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
      </div>
    </div>
    <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
      <div class="weather-box">
        <div class="temp">{{ Math.round(weather.main.temp) }}<span class="degrees">°C</span></div>
        <div class="weather">{{ weather.weather[0].main }}</div>
      </div>
    </div>
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      api_key: process.env.VUE_APP_API_KEY,
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {}
    }
  },
  methods: {
    fetchWeather () {
      fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
      .then(res => {
        return res.json();
      }).then(this.setResults);
    },
    setResults (results) {
      this.weather = results;
      this.weather.main.temp = 15;
    },
    dateBuilder () {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    },
    tempClass() {
      let tClass = 'no-temp';
      console.log(this.weather)
      if (typeof this.weather.main != 'undefined') {
        tClass = 'temp-' + this.weather.main.temp;
      }
      console.log(tClass);
      return tClass;
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,900;1,900&family=Raleway:wght@600;900&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Montserrat', sans-serif;
}

#app {
  background-size: cover;
  background-position: bottom;
  transition: 0.4;
  background: linear-gradient(rgb(42, 157, 211), rgb(22, 129, 230));
}

#app.temp-1 {
  background: linear-gradient(20deg, rgb(255, 255, 255), rgb(60, 193, 255))
}
#app.temp0 {
  background: linear-gradient(10deg, rgb(255, 255, 255), rgb(40, 187, 255))
}

#app.temp1 {
  background: linear-gradient(-350deg, rgb(222, 237, 255), rgb(40, 187, 255))
}
#app.temp2 {
  background: linear-gradient(75deg, rgb(222, 237, 255), rgb(40, 187, 255))
}
#app.temp3 {
  background: linear-gradient(100deg, rgb(222, 237, 255), rgb(40, 187, 255))
}

#app.temp4 {
  background: linear-gradient(20deg, rgb(194, 221, 255), rgb(29, 183, 255))
}
#app.temp5 {
  background: linear-gradient(-310deg, rgb(194, 221, 255), rgb(29, 183, 255))
}

#app.temp6 {
  background: linear-gradient(30deg, rgb(180, 214, 255), rgb(29, 183, 255))
}
#app.temp7 {
  background: linear-gradient(60deg, rgb(180, 214, 255), rgb(29, 183, 255))
}

#app.temp8 {
  background: linear-gradient(rgb(42, 157, 211), rgb(153, 198, 240))
}
#app.temp9 {
  background: linear-gradient( rgb(153, 198, 240), rgb(42, 157, 211))
}

#app.temp10 {
  background: linear-gradient(rgb(58,159,200), rgb(161,201,236))
}
#app.temp11 {
  background: linear-gradient(rgb(58,159,200), rgb(170,204,233))
}
#app.temp12 {
  background: linear-gradient(rgb(90, 129, 179), rgb(179,206,229))
}
#app.temp13 {
  background: linear-gradient(rgb(106, 138, 168), rgb(187,209,226))
}
#app.temp14 {
  background: linear-gradient(rgb(122,169,157), rgb(196,212,222))
}
#app.temp15 {
  background: linear-gradient(rgb(139, 160, 171), rgb(204,215,218))
}
#app.temp16 {
  background: linear-gradient(rgb(163, 174, 136), rgb(212,218,215))
}
#app.temp17 {
  background: linear-gradient(rgb(187,179,114), rgb(230,224,208))
}
#app.temp18 {
  background: linear-gradient(rgb(203,181,104), rgb(238,226,204))
}
#app.temp19 {
  background: linear-gradient(rgb(219,184,93), rgb(247,229,201))
}

#app.temp20 {
  background: linear-gradient(20deg,rgb(235, 186, 82), rgb(255, 232, 197))
}
#app.temp21 {
  background: linear-gradient(50deg,rgb(235, 186, 82), rgb(255, 232, 197))
}
#app.temp22 {
  background: linear-gradient(70deg,rgb(235, 186, 82), rgb(255, 232, 197))
}

#app.temp25 {
  background: linear-gradient(100deg,rgb(247, 186, 54), rgb(252, 180, 113))
}
#app.temp26 {
  background: linear-gradient(100deg,rgb(247, 186, 54), rgb(252, 180, 113))
}
#app.temp27 {
  background: linear-gradient(100deg,rgb(247, 186, 54), rgb(252, 180, 113))
}
#app.temp28 {
  background: linear-gradient(100deg,rgb(212, 92, 12), rgb(250, 146, 35))
}
#app.temp29 {
  background: linear-gradient(100deg,rgb(199, 62, 12), rgb(250, 121, 35))
}
#app.temp30 {
  background: linear-gradient(30deg, rgb(199, 40, 12), rgb(250, 92, 35))
}


#app.temp36, #app.temp37, #app.temp38, #app.temp39, #app.temp40 {
  background: linear-gradient(20deg, rgb(25, 0, 46), rgb(148, 0, 27), rgb(174, 0, 0))
}


main {
  min-height: 100vh;
  padding: 25px;

}

.search-box {
  flex: 4;
  margin-bottom: 30px;
}

.search-box .search-bar {
  font-family: 'Raleway';
  font-weight: 600;
  display: block;
  padding: 10px 16px;

  color: #383838;
  font-size: 13px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  background-color: rgba(255, 255, 255, 0.15);
  border-radius: 16px 16px;
  transition: 0.4s;
}
::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
  color: #545454;
  opacity: 1; /* Firefox */
}

.top-bar {
  display: flex;
}

.search-box .search-bar: focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}

.location-box {
  flex: 6;

}

.location-box .location {
  font-family: 'Raleway', sans-serif;
  font-style: italic;
  font-size: 16px;
  padding: 4px 16px;

  font-weight: 800;
  width: 100%;
  text-align: right;
}

.location-box .date {
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  color: #000;
  font-size: 200px;
  font-weight: 900;
  letter-spacing: -0.05em;
  
  border-radius: 16px;
  margin-top: 15vh;

  font-family: 'Montserrat', sans-serif;
  font-style: italic;
}

.degrees {
  font-size: 0.5em;
  letter-spacing: -0.02em;
  margin-left: 8px;
}

.weather-box .weather {
  font-family: 'Raleway', sans-serif;
  font-size: 22px;
  font-weight: 900;
  margin-top: -30px;
}
</style>
