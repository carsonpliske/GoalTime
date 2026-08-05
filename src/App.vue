<script setup lang="ts">
import { computed } from 'vue'

const categories = [
  { label: 'OPU', rate: 55 },
  { label: 'SHIP', rate: 45 },
  { label: 'S&O', rate: 50 },
  { label: 'S&P', rate: 40 },
  { label: 'O&P', rate: 50 },
]

const hoursList = computed(() => {
  const list: number[] = []
  for (let h = 3.75; h <= 10 + 1e-9; h += 0.25) {
    list.push(Math.round(h * 100) / 100)
  }
  return list
})
</script>

<template>
  <div class="app">
    <div class="content-container">
      <div class="logo-container">
        <img src="/Target.jpg" alt="Target Logo" class="target-logo" />
      </div>
      
      <div class="table-wrapper">
        <table class="goal-table">
          <thead>
            <tr>
              <th>HRS</th>
              <th v-for="cat in categories" :key="cat.label">{{ cat.label }}</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="h in hoursList" :key="h">
              <td class="hour-cell">{{ h.toFixed(2) }}</td>
              <td v-for="cat in categories" :key="cat.label">{{ Math.round(h * cat.rate) }}</td>
            </tr>
          </tbody>
        </table>
      </div>
      
      <div class="version">v1.0.5</div>
    </div>
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
  min-height: -webkit-fill-available;
  width: 100vw;
  background-color: white;
  margin: 0;
  padding: 0;
  padding-top: env(safe-area-inset-top);
  padding-bottom: env(safe-area-inset-bottom);
}

.content-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  padding: 0 20px;
  min-height: calc(100vh - env(safe-area-inset-top) - env(safe-area-inset-bottom));
}

.logo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
  margin-bottom: 20px;
}

.target-logo {
  width: 80px;
  height: 80px;
  object-fit: contain;
}

.table-wrapper {
  width: 100%;
  max-width: 500px;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.goal-table {
  width: 100%;
  border-collapse: collapse;
  table-layout: fixed;
  font-size: clamp(11px, 3.2vw, 15px);
}

.goal-table thead th {
  position: sticky;
  top: 0;
  background-color: #cc0000;
  color: white;
  font-weight: bold;
  padding: 8px 2px;
  text-align: center;
  z-index: 1;
}

.goal-table tbody td {
  padding: 6px 2px;
  text-align: center;
  border-bottom: 1px solid #eee;
  color: #333;
}

.goal-table tbody tr:nth-child(even) {
  background-color: #f8f8f8;
}

.hour-cell {
  font-weight: bold;
  color: #cc0000;
}

.version {
  text-align: center;
  color: #666;
  font-size: 14px;
  margin-top: 20px;
  margin-bottom: 20px;
  padding-bottom: 20px;
}
</style>
