<script setup lang="ts">
import Navbar from '~/components/layout/navbar.vue'
</script>

<template>
  <div class="h-screen">
    <Navbar />
    <main class="h-full mx-auto px-4 sm:px-6 lg:px-8 dark:bg-gray-900">
      <div class="mx-auto py-6">
        <slot/>
      </div>
    </main>
  </div>
</template>



<style scoped>

</style>