<template>
  <div class="w-100 min-vh-100" style="background-color: #fdfbe7;">
    <NavBar />

    <main class="px-4 py-5">
      <SearchBox />
      <div class="mb-5"></div>
      <UsageGuide />
    </main>
  </div>
</template>

<script setup>
import NavBar from '../components/NavBar.vue'
import SearchBox from '../components/SearchBox.vue'
import UsageGuide from '../components/UsageGuide.vue'
</script>
