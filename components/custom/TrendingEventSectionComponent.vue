<script setup>
import { ref, computed } from "vue";
import { useDateFormat } from "@vueuse/core";
import TrendingEventsCardComponent from "@/components/custom/TrendingEventsCardComponent.vue"
import arrow from '@/assets/icons/arrow-up.svg'

const formatEventDate = (dateString, timeString) => {
  const fullDate = new Date(`${dateString}T${timeString}`);
  return useDateFormat(fullDate, "ddd MMM, Do • hA");
};

const { data, error, pending } = await useFetch(
  "https://rendezvous-events.onrender.com/events",
  {
    server: false, // Fetch only on client-side
  }
);

// Extract events from the nested response
// const events = computed(() => (data.value?.data?.allEvents || []).slice(0, 3));

const ITEMS_PER_PAGE = 3;
const currentPage = ref(1);

const paginatedEvents = computed(() => {
  const allEvents = data.value?.data?.allEvents || [];
  const start = (currentPage.value - 1) * ITEMS_PER_PAGE;
  return allEvents.slice(start, start + ITEMS_PER_PAGE);
});

const totalPages = computed(() => {
  const totalEvents = data.value?.data?.allEvents?.length || 0;
  return Math.ceil(totalEvents / ITEMS_PER_PAGE);
});

const goToNextPage = () => {
  if (currentPage.value < totalPages.value) currentPage.value++;
};

const goToPrevPage = () => {
  if (currentPage.value > 1) currentPage.value--;
};
</script>

<template>
  <div class="pb-[100px]">
    <div class="flex items-center justify-between mx-[64px] mb-[47px] mt-[64px]">
      <h1 class="font-[400] text-[32px] leading-[100%]">Trending events</h1>
      <nuxt-link to="/" class="flex items-center space-x-[4px]">
          <p class="text-[16px] text-[#432361] font-[400] leading-[100%] hover:underline">View all trending events</p>
          <img :src="arrow" alt="arrow-icon">
        </nuxt-link>
    </div>

    <!-- Loader / Error -->
    <div v-if="pending" class="text-center text-[#432361] text-xl">
      Loading events, please wait...
    </div>
    <div v-else-if="error" class="text-center text-red-500 text-xl">
      Failed to load events 😢
    </div>

    <!-- Events -->
    <div v-else class="grid grid-cols-1 sm:grid-cols-1 lg:grid-cols-3 gap-[26px] mx-[64px]">
      <trending-events-card-component
        v-for="event in paginatedEvents"
        :key="event.id"
        :image="event.imageUrl"
        :title="event.title"
        :date="formatEventDate(event.date, event.time)"
        :description="event.description"
      />
    </div>
    <div class="flex justify-center items-center gap-4 mt-10">
      <button @click="goToPrevPage" :disabled="currentPage === 1" class="px-4 py-2 bg-[#432361] text-white rounded disabled:opacity-40 hover:opacity-90">
        Prev
      </button>
      <span class="text-[#432361] text-sm">Page {{ currentPage }} of {{ totalPages }}</span>
      <button @click="goToNextPage" :disabled="currentPage === totalPages" class="px-4 py-2 bg-[#432361] text-white rounded disabled:opacity-40 hover:opacity-90">
        Next
      </button>
    </div>
  </div>
</template>
