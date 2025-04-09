<script setup>
import ButtonComponent from "@/components/custom/ButtonComponent.vue";
</script>

<template>
  <div
    class="bg-white rounded-[20px] px-[24px] flex flex-col sm:flex-row items-start sm:items-center sm:justify-between gap-4 sm:gap-0 w-full max-w-[660px] mx-auto"
  >
    <!-- Search Icon + Input -->
    <div class="flex w-full sm:my-[24.5px] sm:mr-[17.33px] items-center space-x-2 flex-1">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-[16px] w-[16px] text-gray-400 mr-[1.5px]"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M21 21l-4.35-4.35m0 0A7.5 7.5 0 1011 18.5a7.5 7.5 0 005.65-1.85z"
        />
      </svg>
      <input
        type="text"
        placeholder="Search for an event"
        class="outline-none w-full placeholder-[#4F4F4F] text-[16px] font-[400] leading-[100%]"
      />
    </div>

    <!-- Divider (hidden on mobile) -->
    <div class="hidden sm:block w-[2px] h-6 bg-[#E0E0E0] sm:mr-[17.33px]"></div>

    <!-- Dropdown -->
    <div class="relative w-full sm:w-auto sm:mr-[17.33px]">
      <select
        class="appearance-none w-full sm:w-auto text-[16px] font-[400] text-[#4F4F4F] pr-[30px] bg-transparent focus:outline-none"
      >
        <option>Categories</option>
        <option>Music</option>
        <option>Events</option>
        <option>TV Shows</option>
      </select>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="w-4 h-4 text-gray-500 absolute right-0 top-1/2 transform -translate-y-1/2"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M19 9l-7 7-7-7"
        />
      </svg>
    </div>

    <!-- Search Button -->
    <div class="w-full sm:w-auto">
      <button-component text="Search" class="w-full sm:w-auto" />
    </div>
  </div>
</template>
