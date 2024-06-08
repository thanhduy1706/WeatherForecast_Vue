<script setup>
defineProps({
  place: Object
})
</script>

<template>
  <div
    class="absolute inset-x-0 bottom-0 rounded-xl p-7 bg-white/70 backdrop-blur-lg text-slate-900"
  >
    <!-- Close button -->
    <div class="mb-5 transition-all duration-200 flexCenter hover:text-red-500">
      <button @click="$emit('close-info')" class="p-1" aria-label="Close">
        <i class="text-3xl fa-solid fa-xmark"></i>
      </button>
    </div>

    <div class="gap-6 mb-5 flexCenter">
      <!-- Wind speed -->
      <div class="flex-1 text-center">
        <i class="text-2xl fa-solid fa-wind mb"></i>
        <p class="text-lg font-bold">{{ place.current.wind_kph }} km/h</p>
        <p>wind</p>
      </div>

      <!-- Humidity level -->
      <div class="flex-1 text-center">
        <i class="text-2xl fa-solid fa-droplet mb"></i>
        <p class="text-lg font-bold">{{ place.current.humidity }}%</p>
        <p>humidity</p>
      </div>

      <!-- Precipitation -->
      <div class="flex-1 text-center">
        <i class="text-2xl fa-solid fa-umbrella mb"></i>
        <p class="text-lg font-bold">{{ place.current.precip_mm }} mm</p>
        <p>precipitation</p>
      </div>
    </div>
    <div class="gap-6 mb-10 flexCenter">
      <!-- Wind direction -->
      <div class="flex-1 text-center">
        <i class="text-2xl fa-solid fa-fan mb"></i>
        <p class="text-lg font-bold">{{ place.current.wind_dir }}</p>
        <p>direction</p>
      </div>

      <!-- Feels like -->
      <div class="flex-1 text-center">
        <i class="text-2xl fa-solid fa-temperature-half mb"></i>
        <p class="text-lg font-bold">{{ Math.round(place.current.feelslike_c) }}</p>
        <p>Feels</p>
      </div>

      <!-- UV -->
      <div class="flex-1 text-center">
        <i class="text-2xl fa-solid fa-sun mb"></i>
        <p class="text-lg font-bold">{{ place.current.uv }}</p>
        <p>UV index</p>
      </div>
    </div>

    <!-- Last update and delete -->
    <div class="gap-8 flexCenter">
      <div>
        <h3 class="text-sm font-bold text-slate-900/50">Last update</h3>
        <p class="text-sm">{{ place.current.last_updated }}</p>
      </div>
      <button @click="$emit('remove-place')" aria-label="Remove place" class="mr-2">
        <i class="fa-solid fa-trash"></i>
      </button>
    </div>
  </div>
</template>
