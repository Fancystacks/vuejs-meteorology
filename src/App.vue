<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input
          type="text"
          class="search-bar"
          placeholder="Search a location . . ."
          v-model="query"
          @keypress="fetchClimate"
        />
      </div>
      <div class="climate-wrapper" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">
            {{ weather.name }}, {{ weather.sys.country }}
          </div>
          <div class="date">Monday February 4th, 2020</div>
        </div>
        <div class="climate-box"></div>
        <div class="temp">65°F</div>
        <div class="condition">Rain</div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      api_key: "5650ba04d76cc8ddc64d65a07cda4c4a",
      baseurl: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {},
    };
  },
  methods: {
    fetchClimate(event) {
      if (event.key == "Enter") {
        fetch(
          `${this.baseurl}weather?q=${this.query}&units=imperial&APPID=${this.api_key}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.setResult);
      }
    },
    setResult(result) {
      this.weather = result;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", san-serif;
}

#app {
  background-image: url("https://user-images.githubusercontent.com/38336934/80895764-b442f180-8ca5-11ea-8391-0e52ba7b443a.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

main {
  min-height: 100vh;
  padding: 25px;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.6));
}

.search-box {
  margin: 40px 0 60px 0;
  width: 100%;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;
  opacity: 0.5;
  transition: 0.5s;
  border-radius: 20px;
  box-shadow: 8 15px 8px -6px black;
  font-size: 30px;
}

.search-box .search-bar:focus {
  opacity: 0.8;
}

.location-box .location {
  color: white;
  font-size: 58px;
  font-weight: 650;
  text-align: center;
  text-shadow: 10px 16px 20px rgba(0, 0, 0, 0.25);
  font-family: "Montserrat", san-serif;
  margin-bottom: 15px;
}

.location-box .date {
  color: white;
  font-size: 28px;
  font-weight: 150;
  opacity: 0.5;
  text-align: center;
  text-shadow: 4px 6px rgba(0, 0, 0, 0.25);
  font-family: "Montserrat", san-serif;
}

.climate-wrapper .temp {
  display: inline-block;
  padding: 15px 30px;
  font-size: 110px;
  font-weight: 600;
  text-shadow: 9px 11px 14px rgba(0, 0, 0, 0.25);
}

.climate-wrapper {
  text-align: center;
  color: white;
  background-color: rgba(255, 255, 255, 0.25);
  padding: 30px;
  border-radius: 30px;
  box-shadow: 9px 11px 24px rgba(0, 0, 0, 0.25);
}

.climate-wrapper .condition {
  font-size: 50px;
  color: white;
  font-weight: 200;
  text-shadow: 9px 11px 14px rgba(0, 0, 0, 0.25);
}
</style>
