<script setup>
import { ref } from 'vue'
import BorderLine from './BorderLine.vue'
import WeatherForecastDay from './WeatherForecastDay.vue'
import WeatherInfo from './WeatherInfo.vue'

defineProps({
  place: Object
})

const emit = defineEmits(['delete-place'])

const showDetail = ref(false)

const removePlace = (placeName) => {
  emit('delete-place', placeName)
  showDetail.value = false
}
</script>

<template>
  <div
    :class="place.current.is_day === 1 ? 'bg-day' : 'bg-night'"
    class="relative max-w-xl gap-6 p-10 mb-6 overflow-hidden text-white rounded-lg shadow-xl"
  >
    <!-- Location & time -->
    <div class="flex-col mb-2 flexCenter">
      <div class="flex items-center gap-2">
        <i class="fa-solid fa-location-dot"></i>
        <h1 class="text-xl">{{ place.location.name }}</h1>
      </div>
      <div class="gap-2 flexCenter">
        <i class="fa-solid fa-clock"></i>
        <h1 class="text-xl">
          {{ String(new Date(place.location.localtime).getHours()).padStart(2, '0') }}:{{
            String(new Date(place.location.localtime).getMinutes()).padStart(2, '0')
          }}
        </h1>
      </div>
    </div>

    <!-- current weather -->
    <div class="flex-col flexCenter">
      <div class="flexCenter">
        <img :src="place.current.condition.icon" alt="condition icon" width="100" class="" />
        <h1 class="text-center text-7xl">{{ Math.round(place.current.temp_c) }}&deg;</h1>
      </div>
      <p class="text-2xl">{{ place.current.condition.text }}</p>
    </div>

    <BorderLine />

    <!-- forecast -->
    <div v-for="(day, idx) in place.forecast.forecastday" :key="idx">
      <WeatherForecastDay :day="day" />
    </div>

    <!-- info -->
    <Transition name="fade">
      <div v-show="showDetail">
        <WeatherInfo
          :place="place"
          @close-info="showDetail = false"
          @remove-place="removePlace(place.location.name)"
        />
      </div>
    </Transition>

    <!-- forecast btn -->
    <div class="flex items-center justify-end gap-1 mt-10">
      <button @click="showDetail = true">
        More <i class="-mb-px text-sm fa-solid fa-arrow-right"></i>
      </button>
    </div>
  </div>
</template>
