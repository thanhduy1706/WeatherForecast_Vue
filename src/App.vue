<script setup>
import { ref } from 'vue'
import SearchInput from './components/SearchInput.vue'
import WeatherCard from './components/WeatherCard.vue'

const places = ref([])

const addPlace = (data) => {
  places.value.push(data)
}

const deletePlace = (name) => {
  if (confirm('Are you sure')) {
    places.value = places.value.filter((p) => p.location.name !== name)
  }
}
</script>
<template>
  <main class="flex-col flexCenter">
    <!-- Date -->
    <div class="mb-6 text-2xl font-bold text-center text-slate-200">
      Today is
      <div class="italic">
        {{
          new Date().toLocaleDateString('en-us', {
            weekday: 'long',
            year: 'numeric',
            month: 'long',
            day: 'numeric'
          })
        }}
      </div>
    </div>

    <!-- Search -->
    <div class="">
      <SearchInput @place-data="addPlace" />
    </div>

    <!-- Weather cards -->
    <div class="grid grid-cols-1 gap-4 mt-20 sm:grid-cols-auto">
      <div v-for="(place, idx) in places" :key="idx">
        <WeatherCard :place="place" @delete-place="deletePlace" />
      </div>
    </div>
  </main>
</template>
