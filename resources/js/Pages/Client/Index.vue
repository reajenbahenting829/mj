<template>
    <div>
      <Head title="Clients" />
      <AppLayout>
        <template #header>
          <h2 class="font-semibold text-2xl text-gray-800 leading-tight"></h2>
        </template>
        <h2 class="font-semibold text-2xl text-gray-800 leading-tight">Clients List</h2>

        <div class="py-12 max-w-7xl mx-auto sm:px-6 lg:px-8">
          <div class="flex flex-wrap">
            <!-- Client Cards -->
            <ClientCard
              v-for="client in clientsList"
              :key="client.id"
              :client="client"
            />
          </div>

          <!-- Paginator -->
          <div class="flex justify-center items-center mt-4">
            <Pagination
              :links="clients.links"
              :currentPage="clients.current_page"
              :totalPages="clients.total"
              pageRange="4"
            />
          </div>
        </div>
      </AppLayout>
    </div>
  </template>

  <script setup>
  import AppLayout from '@/Layouts/AppLayout.vue';
  import ClientCard from '@/Components/ClientCard.vue';
  import Pagination from '@/Components/Pagination.vue';
  import { Head } from '@inertiajs/vue3';

  const props = defineProps({
    clients: Object,
  });

  const clientsList = props.clients.data;
  </script>
