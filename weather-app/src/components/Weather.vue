<template>
  <main>
    <div class="app flex-col">
      <h1 class="text-center font-bold mt-5">Weather App</h1>
      <div class="search-box flex justify-center items-center p-7">
        <input
          type="text"
          placeholder="Search for a city..."
          class="focus:outline-none border-black bg-transparent content-center w-96 border-2 p-4 rounded-full font-bold"
        />
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-9 w-9 cursor-pointer"
          fill="black"
          viewBox="0 0 24 24"
          stroke="white"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z"
          />
        </svg>
      </div>
      <div
        class="info-box bg-gray-800 shadow-lg shadow-gray-500/50 text-white font-bold"
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
            >Ankara, TR
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
            >Thursday 23 June 2022
          </div>
        </div>
        <div class="weather-box">
          <div class="temp justify-center items-center flex border-b-2 p-4">
            9°
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
            >Cloud
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
    };
  },
};
</script>
