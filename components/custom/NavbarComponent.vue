<script setup>

const navLinks = [
  { name: 'Discover', to: '/discover' },
  { name: 'About Us', to: '/about' },
  { name: 'FAQ', to: '/faq' },
  { name: 'Contact Us', to: '/contact' }
]

</script>
<template>
    <nav class="absolute z-10 bg-[#FFFFFF99] rounded-[20px] mx-[64px] mt-[50px] py-[12px] border border-red-500">
      <div class=" flex items-center justify-between mx-[24px] border border-green-500 space-x-[258.5px]">
        <div>
            <div class="font-[400] text-[32px] leading-[100%] text-[#432361]">rendezvous</div>
        </div>
        <!-- Center: Nav Links -->
        <ul class="flex space-x-6 justify-center flex-1">
          <li v-for="(link, index) in navLinks" :key="index">
            <nuxt-link
              :to="link.to"
              class="text-gray-700 hover:text-blue-600 transition-colors duration-300"
            >
              {{ link.name }}
          </nuxt-link>
          </li>
        </ul>
  
        <!-- Right: Auth Buttons -->
        <div class="flex items-center space-x-4">
          <nuxt-link to="/login" class="text-gray-700 hover:text-blue-600 transition-colors mr-[24px]">
            Log In
          </nuxt-link>
          <nuxt-link
            to="/signup"
            class="bg-purple-600 text-white px-4 py-2 rounded-md hover:bg-purple-700 transition-colors"
          >
            Sign Up
          </nuxt-link>
        </div>
        
      </div>
    </nav>
  </template>