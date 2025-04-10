<script setup>
import { useRoute } from 'vue-router'
import { useDateFormat } from '@vueuse/core'
import { ref, computed } from 'vue'

const route = useRoute()
const eventId = route.params.id

const formatEventDate = (dateString, timeString) => {
  const fullDate = new Date(`${dateString}T${timeString}`)
  return useDateFormat(fullDate, 'ddd MMM, Do • hA').value.toLowerCase()
}

// Fetch single event
const { data, pending, error } = await useFetch(
  `https://rendezvous-events.onrender.com/events/${eventId}`,
  {
    server: false // Client-side only
  }
)

const event = computed(() => data.value?.data?.event || null)
</script>

<template>
  <div class=" mx-[39px] py-10 px-6">
    <div v-if="pending" class="text-center text-[#432361] text-lg">
      Loading event...
    </div>
    <div v-else-if="error" class="text-center text-red-500 text-lg">
      Failed to load event 😢
    </div>

    <!-- Event Details -->
    <div v-else-if="event" class="space-y-6">
      <img :src="event.imageUrl" alt="Event Image" class="w-[1311px] h-auto rounded-[10px]" />

      <!-- content -->
      <div class="grid grid-cols-4 border gap-x-[37px]">
        <div class="border border-red-500 col-span-3">
            <h1 class="text-3xl font-bold text-[#432361]">
        {{ event.title }}
      </h1>

      <p class="text-gray-500 text-sm">
        {{ formatEventDate(event.date, event.time) }}
      </p>

      <p class="text-lg text-gray-800 leading-relaxed">
        {{ event.description }}
      </p>
        </div>
        <!-- maps -->
        <div class="border border-blue-500">
            pictures
        </div>
      </div>
    </div>
  </div>
</template>
