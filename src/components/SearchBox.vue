<template>
  <div class="search-wrapper">
    <!-- 新增标题 -->
    <h2 class="search-title">FIND YOUR PARK FAST</h2>

    <div class="search-container">
      <input
        v-model="query"
        type="text"
        class="search-input"
        placeholder="Enter your destination..."
      />
      <button class="search-btn" @click="search">Find Parking</button>
    </div>
  </div>
</template>


<script setup>
import { ref } from 'vue'

const query = ref('')

function search() {
  if (!query.value.trim()) return
  console.log('Searching for:', query.value)
}
</script>

<style scoped>
.search-wrapper {
  text-align: center;
  margin-bottom: 50px;
}

.search-title {
  font-weight: bold;
  margin-bottom: 50px;
  font-size: 24px;
  color: #333;
}


.search-container {
  display: flex;
  max-width: 700px;
  margin: 0 auto;
  background: #999; /* 自定义背景色 */
  border-radius: 40px;
  padding: 5px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.search-input {
  flex: 1;
  border: none;
  border-radius: 40px 0 0 40px;
  padding: 12px 20px;
  font-size: 16px;
  background: transparent;
  color: white;
  outline: none;
}

.search-input::placeholder {
  color: #eee;
}

.search-btn {
  border: none;
  background: white;
  color: #333;
  font-weight: bold;
  border-radius: 50px;
  padding: 12px 24px;
  cursor: pointer;
  transition: background 0.2s;
}

.search-btn:hover {
  background: #f0f0f0;
}
</style>
