<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input
          type="text"
          class="search-bar"
          placeholder="Search a location . . ."
        />
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
    };
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
  margin-bottom: 40px;
  width: 100%;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;
  opacity: 0.5;
  border-radius: 100px;
  box-shadow: 8 15px 8px -6px black;
  font-size: 30px;
}

.search-box .search-bar:focus {
  opacity: 0.9;
}
</style>
