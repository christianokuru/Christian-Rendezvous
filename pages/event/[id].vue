<script setup>
import { useRoute } from "vue-router";
import { useDateFormat } from "@vueuse/core";
import { ref, computed } from "vue";
import ButtonComponent from "~/components/custom/ButtonComponent.vue";

const route = useRoute();
const eventId = route.params.id;

const formatEventDate = (dateString, timeString) => {
  const fullDate = new Date(`${dateString}T${timeString}`);
  return useDateFormat(fullDate, "ddd MMM, Do • hA");
};

// Fetch single event
const { data, pending, error } = await useFetch(
  `https://rendezvous-events.onrender.com/events/${eventId}`,
  {
    server: false, // Client-side only
  }
);

const event = computed(() => data.value?.data?.event || null);
</script>

<template>
  <div class="mx-[39px] py-10 px-6">
    <div v-if="pending" class="text-center text-[#432361] text-lg">
      Loading event...
    </div>
    <div v-else-if="error" class="text-center text-red-500 text-lg">
      Failed to load event 😢
    </div>

    <!-- Event Details -->
    <div v-else-if="event" class="space-y-6">
      <img
        :src="event.imageUrl"
        alt="Event Image"
        class="w-[1311px] h-[480px] object-cover rounded-[10px]"
      />

      <!-- content -->
      <div class="grid grid-cols-4 gap-x-[37px]">
        <div class="col-span-3">
          <h1
            class="font-[500] text-[24px] leading-[100%] text-[#000000] mb-[16px]"
          >
            {{ event.title }}
          </h1>
          <div class="space-y-[8px] mb-[50px]">
            <div class="flex items-center space-x-[2.5px]">
              <img src="/assets/icons/Calendar.svg" alt="calendar-icon" />
              <p class="font-[400] text-[16px] leading-[100%]">
                {{ formatEventDate(event.date, event.time) }}
              </p>
            </div>
            <div class="flex items-center space-x-[2.5px]">
              <img src="/assets/icons/Location.svg" alt="location-icon" />
              <p class="font-[400] text-[16px] leading-[100%]">
                {{ event.address, event.city }}, {{ event.country }}
              </p>
            </div>
            <div class="flex items-center space-x-[2.5px]">
              <img src="/assets/icons/Calendar.svg" alt="calendar-icon" />
              <p class="font-[400] text-[16px] leading-[100%] capitalize">
                {{ event.category }}
              </p>
            </div>
            <div class="flex items-center space-x-[2.5px]">
              <img src="/assets/icons/User.svg" alt="user-icon" />
              <p class="font-[400] text-[16px] leading-[100%]">
                {{ event.organizer.name }}
              </p>
            </div>
          </div>

          <div class="pb-[20px]">
            <h1 class="font-[600] text-[16px] leading-[100%] mb-[20px]">
              Event description
            </h1>
            <p class="font-[400] text-[16px] leading-[100%]">
              {{ event.description }}
            </p>
          </div>
          <div>
            <h1 class="font-[600] text-[16px] leading-[100%] mb-[20px]">
              Ticket pricing
            </h1>
            <div class="flex items-center mb-[48px] space-x-[64px]">
              <div>
                <h1 class="font-[500] text-[20px] leading-[100%]">Single</h1>
                <p
                  class="font-[500] text-[20px] leading-[100%] mt-[8px] text-[#9B51E0]"
                >
                  NGN {{ event.price }}
                </p>
              </div>
              <div>
                <h1 class="font-[500] text-[20px] leading-[100%]">Pair</h1>
                <p
                  class="font-[500] text-[20px] leading-[100%] mt-[8px] text-[#9B51E0]"
                >
                  NGN {{ event.price }}
                </p>
              </div>
            </div>
            <button-component text="Buy now" />
          </div>
        </div>
        <!-- maps -->
        <div>
          <div class="mb-[50px]">
            <div class="mb-[20px]">
              <h1 class="font-[600] text-[16px] leading-[100%] text-[#000000]">
                Contact organizers
              </h1>
            </div>
            <div class="flex items-center space-x-[24px]">
              <img src="/assets/icons/email.svg" alt="email" />
              <img src="/assets/icons/x.svg" alt="" />
              <img src="/assets/icons/insta.svg" alt="" />
            </div>
          </div>
          <!-- map -->
          <div>
            <p class="font-[600] text-[16px] leading-[100%] text-[#000000]">
              Directions
            </p>
            <!-- Map Embed -->
            <div class="mt-[20px]">
              <iframe
                v-if="event.lat && event.long"
                :src="`https://www.google.com/maps?q=${event.lat},${event.long}&hl=es;z=14&output=embed`"
                width="100%"
                height="400"
                style="border: 0"
                allowfullscreen=""
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
