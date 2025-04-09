<script setup>
import { ref, computed } from 'vue'
import TrendingEventsCardComponent from '@/components/custom/TrendingEventsCardComponent.vue'

// Pagination states
const currentPage = ref(1)
const itemsPerPage = 3

// useFetch call (Nuxt handles server-side rendering and reactivity here!)
const { data: events, pending, error } = await useFetch('https://rendezvous-events.onrender.com/events')

// Computed pagination logic
// const totalPages = computed(() => {
//   return events.value ? Math.ceil(events.value.length / itemsPerPage) : 0
// })

// const paginatedEvents = computed(() => {
//   if (!events.value) return []
//   const start = (currentPage.value - 1) * itemsPerPage
//   return events.value.slice(start, start + itemsPerPage)
// })

// // Pagination actions
// function nextPage() {
//   if (currentPage.value < totalPages.value) currentPage.value++
// }

// function prevPage() {
//   if (currentPage.value > 1) currentPage.value--
// }
</script>

<template>
  <div>
    <div class="flex items-center justify-between mx-[64px] mb-[47px] mt-[64px]">
      <h1 class="font-[400] text-[32px] leading-[100%]">Trending events</h1>
      <nuxt-link to="/signup">
        <p class="font-[400] text-[16px] leading-[100%] text-[#432361] hover:underline">
          View all trending events
        </p>
      </nuxt-link>
    </div>

    <!-- Loader / Error -->
    <div v-if="pending" class="text-center text-[#432361] text-lg">Loading events...</div>
    <div v-else-if="error" class="text-center text-red-500 text-lg">Failed to load events 😢</div>

    <!-- Events -->
    <div v-else class="grid grid-cols-1 sm:grid-cols-1 lg:grid-cols-3 gap-[26px] mx-[64px]">
      <trending-events-card-component
        v-for="(event, index) in paginatedEvents"
        :key="index"
        :image="event.image"
        :title="event.title"
        :date="event.date"
        :time="event.time"
        :description="event.description"
      />
    </div>

    <!-- Pagination controls -->
    <!-- <div v-if="events && events.length > 0" class="flex items-center justify-center mt-8 space-x-4">
      <button
        @click="prevPage"
        :disabled="currentPage === 1"
        class="px-4 py-2 bg-[#432361] text-white rounded disabled:opacity-50"
      >
        Previous
      </button>
      <span class="text-lg font-semibold text-[#432361]">Page {{ currentPage }} of {{ totalPages }}</span>
      <button
        @click="nextPage"
        :disabled="currentPage === totalPages"
        class="px-4 py-2 bg-[#432361] text-white rounded disabled:opacity-50"
      >
        Next
      </button>
    </div> -->
  </div>
</template>
