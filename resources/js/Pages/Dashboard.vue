<template>
    <div>
      <Head title="Dashboard" />

      <AppLayout>
        <template #header>
          <h2 class="font-semibold text-2xl text-gray-800 leading-tight">

          </h2>
        </template>
        <h2 class="font-semibold text-2xl text-gray-800 leading-tight">
            Welcome to Your Dashboard
          </h2>

        <div class="p-4">
          <h2 class="font-semibold text-2xl text-gray-800 leading-tight">
            Dashboard Overview
          </h2>
          <p class="text-gray-600 mt-2">
            Here you can view important information about your application.
          </p>

          <!-- Display the client count -->
          <div class="mt-4">
            <h3 class="text-lg font-semibold">Client Count</h3>
            <p class="text-gray-600">{{ clientCount }}</p>
          </div>

          <!-- Add more content as needed -->

          <!-- Example: Recent Activity -->
          <div class="mt-8">
            <h3 class="text-lg font-semibold">Recent Activity</h3>
            <ul>
              <li class="text-gray-600">User A updated their profile.</li>
              <li class="text-gray-600">New support ticket created by User B.</li>
              <!-- Add more activity items here -->
            </ul>
          </div>
        </div>
      </AppLayout>
    </div>
  </template>

  <script setup>
  import AppLayout from '@/Layouts/AppLayout.vue';
  import { Head, Link } from '@inertiajs/vue3';

  const prop = defineProps({
      clientCount: Number
  })
  </script>
