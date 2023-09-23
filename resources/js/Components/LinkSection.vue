<script setup>
import { Link } from '@inertiajs/vue3';

defineProps({
    isCollapsed: Boolean
})
</script>

<template>
    <div class="main-nav ">
    <div class="flex flex-col space-y-3 mt-4" :class="{ 'items-center' : isCollapsed }">
        <Link href="/dashboard" class="px-2 py-1.5 rounded-lg text-sm text-white hover:bg-white hover:text-black duration-75 space-x-2">
            <i class="fa-solid fa-chart-line"></i>
            <span v-show="!isCollapsed">Dashboard</span>
        </Link>
        <Link href="/clients" class="px-2 py-1.5 rounded-lg text-sm text-white hover:bg-white hover:text-black duration-75 space-x-2">
            <i class="fa-solid fa-user-tie"></i>
            <span v-show="!isCollapsed">Clients</span>
        </Link>
         <Link href="/" class="px-2 py-1.5 rounded-lg text-sm text-white hover:bg-white hover:text-black duration-75 space-x-2">
              <i class="fa-solid fa-user"></i>  <span>Profile</span></Link>
        <Link href="/" class="px-2 py-1.5 rounded-lg text-sm text-white hover:bg-white hover:text-black duration-75 space-x-2">
            <i class="fa-solid fa-phone-volume"></i> <span>Contact Us</span></Link>

        <Link :href="route('logout')" method="post" class="px-2 py-1.5 rounded-lg text-sm text-white hover:bg-white hover:text-black duration-75 space-x-2 ">
                <i class="fa-solid fa-right-from-bracket"></i> <span :hidden="hidden">Logout</span>
     </Link>
    </div>
    </div>
</template>
