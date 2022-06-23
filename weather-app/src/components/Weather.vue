<template>
  <main>
    <div
      class="app flex-col"
    >
      <h1 class="text-center font-bold mt-5">Weather App</h1>
      <div class="search-box flex justify-center items-center p-7">
        <input
          type="text"
          placeholder="Search for a city..."
          v-model="query"
          @keypress="fetchWeather"
          class="focus:outline-none border-black bg-transparent content-center w-96 border-2 p-4 rounded-full font-bold"
        />
      </div>
      <div
        class="info-box bg-gray-800 shadow-lg shadow-gray-500/50 text-white font-bold"
        v-if="typeof weather.main != 'undefined'"
      >
        <div class="location-box mt-10">
          <div class="location justify-center items-center flex border-b-2 p-4">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-4 w-4 mr-3"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
              />
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
              /></svg
            >{{ weather.name }} , {{ weather.sys.country }}
          </div>
          <div class="date justify-center items-center flex border-b-2 p-4">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-4 w-4 mr-3"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
              /></svg
            >{{ dateBuilder() }}
          </div>
        </div>
        <div class="weather-box">
          <div class="temp justify-center items-center flex border-b-2 p-4">
            {{ Math.round(weather.main.temp) }}°c
          </div>
          <div class="weather justify-center items-center flex p-4">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-4 w-4 mr-3"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M3 15a4 4 0 004 4h9a5 5 0 10-.1-9.999 5.002 5.002 0 10-9.78 2.096A4.001 4.001 0 003 15z"
              /></svg
            >{{ weather.weather[0].main }}
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Weather",

  data() {
    return {
      api_key: "960b4ed2947ff8688b76dc2ddca6ca7c",
      url_base: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {},
    };
  },
  methods: {
    fetchWeather(e) {
      if (e.key == "Enter") {
        fetch(
          `${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.setResults);
      }
    },
    setResults(results) {
      this.weather = results;
      this.query = "";
    },
    dateBuilder() {
      let d = new Date();
      let months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      let days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ];
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    },
  },
};
</script>
