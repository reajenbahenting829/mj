<template>
    <div class="flex min-h-screen bg-gray-300">
      <!-- Sidebar -->
      <div
         class="sticky top-0 z-10 min-h-screen duration-150"
        :class="[!isCollapsed ? 'w-64' : 'w-16',
          selectedColor == 'Red' ? 'bg-red-600' : 'bg-black',
          selectedColor == 'Green' ? 'bg-green-600' : 'bg-black',
          selectedColor == 'Blue' ? 'bg-blue-600' : 'bg-black']"

      >
        <div class="relative p-4">
          <!-- Sidebar Collapse Trigger -->
          <span @click="collapseSidebar" class="collapse-trigger text-2xl absolute top-4 -right-8 text-gray-400 hover:text-gray-300">
            <i :class="isCollapsed ? 'fa-solid fa-bars-right' : 'fa-solid fa-bars-left'" class="fa-solid fa-bars"></i>
          </span>
          <SidebarComponent :isCollapsed="isCollapsed" />

          <select v-model="selectedColor" id="color" class="rounded-lg text-sm mt-5">
            <option value="">Select a Color</option>
            <option v-for="(color, index) in themeColors" :key="index" :value="color">{{ color }}</option>
        </select>
        </div>
      </div>

      <!-- Main Content -->
      <div class="flex-1 h-screen">
        <!-- Page Heading -->
        <header v-if="$slots.header" class="page-header bg-gray-200 border-b border-gray-300">
          <div class="flex justify-between items-center max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
            <slot name="header" />
            <!-- User Dropdown -->
            <div class="user-dropdown hidden sm:flex sm:items-center sm:ml-6">
              <div class="ml-3 relative">
                <Dropdown align="right" width="48">
                  <!-- Dropdown Trigger -->
                  <template #trigger>
                    <button class="user-dropdown-trigger inline-flex items-center px-3 py-2 border border-transparent text-sm leading-4 font-medium rounded-md text-gray-500 bg-white hover:text-gray-700 focus:outline-none transition ease-in-out duration-150">
                      {{ $page.props.auth.user.name }}
                      <svg class="ml-2 -mr-0.5 h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
                      </svg>
                    </button>
                  </template>
                  <!-- Dropdown Content -->
                  <template #content>
                    <DropdownLink :href="route('profile.edit')">Profile</DropdownLink>
                    <DropdownLink :href="route('logout')" method="post" as="button">Log Out</DropdownLink>
                  </template>
                </Dropdown>
              </div>
            </div>
          </div>
        </header>

        <!-- Page Content -->
        <main class="page-content p-3">
          <slot />
        </main>
      </div>
    </div>
  </template>

  <script setup>
  import Dropdown from '@/Components/Dropdown.vue';
  import DropdownLink from '@/Components/DropdownLink.vue';
  import SidebarComponent from '@/Components/SidebarComponent.vue';
  import { ref, provide } from 'vue';

  const isCollapsed = ref(false);

  const collapseSidebar = () => {
    isCollapsed.value = !isCollapsed.value;
  };

  const selectedColor = ref('')
  provide('color', selectedColor)

  const themeColors =ref([
    'Blue',
    'Red',
    'Green'
  ])
  </script>
