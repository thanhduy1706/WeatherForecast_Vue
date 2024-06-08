<script setup>
import { reactive } from 'vue'

const emit = defineEmits(['place-data'])

const searchTerm = reactive({
  query: '',
  timeout: null,
  results: null
})

const handleSearch = () => {
  clearTimeout(searchTerm.timeout)
  searchTerm.timeout = setTimeout(async () => {
    // console.log(searchTerm.query)

    if (searchTerm.query !== '') {
      const res = await fetch(
        `https://api.weatherapi.com/v1/search.json?key=12974f50fc4f4222ae172246240706&q=${searchTerm.query}`
      )
      const data = await res.json()
      searchTerm.results = data
      console.log(data)
    } else {
      searchTerm.results = null
    }
  }, 200)
}

const getWeather = async (id) => {
  const res = await fetch(
    `https://api.weatherapi.com/v1/forecast.json?key=12974f50fc4f4222ae172246240706&q=id:${id}&days=3&aqi=yes&alerts=no`
  )
  const data = await res.json()
  emit('place-data', data)

  // console.log(data)

  searchTerm.query = ''
  searchTerm.results = null
}
</script>

<template>
  <div class="">
    <!-- {{ searchTerm.query }} -->
    <!-- search field -->
    <form>
      <div
        class="flex items-center w-screen max-w-xs px-1 border-2 rounded-full shadow-lg sm:max-w-xl bg-slate-200 hover:border-indigo-300"
      >
        <i class="p-4 text-indigo-600 fa-solid fa-magnifying-glass"></i>
        <input
          type="text"
          placeholder="Search for a place"
          class="w-full p-2 border-0 rounded-full outline-0"
          v-model="searchTerm.query"
          @input="handleSearch"
        />
      </div>
    </form>

    <!-- search suggestions -->
    <div class="my-2 rounded-full shadow-lg bg-slate-200">
      <div v-if="searchTerm.results !== null">
        <div v-for="place in searchTerm.results" :key="place.id">
          <button
            @click="getWeather(place.id)"
            class="w-full px-3 my-2 text-left hover:text-indigo-600"
          >
            {{ place.name }}, {{ place.country }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
