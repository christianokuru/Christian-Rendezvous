<script setup>

const navLinks = [
  { name: 'Discover', to: '/discover' },
  { name: 'About Us', to: '/about' },
  { name: 'FAQ', to: '/faq' },
  { name: 'Contact Us', to: '/contact' }
]

</script>
<template>
    <nav class="absolute z-10 w-[1312px]  bg-[#FFFFFF99] rounded-[20px] mx-auto mt-[50px] py-4 border border-red-500">
      <div class="mx-auto flex items-center justify-between">
        <div>
            <div class="font-[400] text-[32px] leading-[100%] text-[#432361]">rendezvous</div>
        </div>
        <!-- Center: Nav Links -->
        <ul class="flex space-x-6 justify-center flex-1">
          <li v-for="(link, index) in navLinks" :key="index">
            <NuxtLink
              :to="link.to"
              class="text-gray-700 hover:text-blue-600 transition-colors duration-300"
            >
              {{ link.name }}
            </NuxtLink>
          </li>
        </ul>
  
        <!-- Right: Auth Buttons -->
        <div class="flex items-center space-x-4">
          <NuxtLink to="/login" class="text-gray-700 hover:text-blue-600 transition-colors">
            Log In
          </NuxtLink>
          <NuxtLink
            to="/signup"
            class="bg-purple-600 text-white px-4 py-2 rounded-md hover:bg-purple-700 transition-colors"
          >
            Sign Up
          </NuxtLink>
        </div>
        
      </div>
    </nav>
  </template>