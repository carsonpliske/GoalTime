<script setup lang="ts">
import { ref, computed } from 'vue'

const opuHours = ref<number | null>(null)
const shipHours = ref<number | null>(null)
const shipOpuHours = ref<number | null>(null)
const shipPackHours = ref<number | null>(null)
const opuPackHours = ref<number | null>(null)

const opuUnitGoal = computed(() => {
  if (opuHours.value === null || opuHours.value === 0) return ''
  return opuHours.value * 55
})

const shipUnitGoal = computed(() => {
  if (shipHours.value === null || shipHours.value === 0) return ''
  return shipHours.value * 45
})

const shipOpuGoal = computed(() => {
  if (shipOpuHours.value === null || shipOpuHours.value === 0) return ''
  return shipOpuHours.value * 50
})

const shipPackGoal = computed(() => {
  if (shipPackHours.value === null || shipPackHours.value === 0) return ''
  return shipPackHours.value * 40
})

const opuPackGoal = computed(() => {
  if (opuPackHours.value === null || opuPackHours.value === 0) return ''
  return opuPackHours.value * 50
})
</script>

<template>
  <div class="app">
    <div class="content-container">
      <div class="logo-container">
        <img src="/Target.jpg" alt="Target Logo" class="target-logo" />
      </div>
      
      <div class="calculators">
        <div class="calculator">
          <label class="calculator-label">OPU UNIT GOAL</label>
          <div class="input-container">
            <input 
              v-model.number="opuHours" 
              type="number" 
              inputmode="numeric"
              placeholder="Hours"
              class="calculator-input"
            />
            <div class="result">{{ opuUnitGoal }}</div>
          </div>
        </div>
        
        <div class="calculator">
          <label class="calculator-label">SHIP UNIT GOAL</label>
          <div class="input-container">
            <input 
              v-model.number="shipHours" 
              type="number" 
              inputmode="numeric"
              placeholder="Hours"
              class="calculator-input"
            />
            <div class="result">{{ shipUnitGoal }}</div>
          </div>
        </div>
        
        <div class="calculator">
          <label class="calculator-label">SHIP & OPU GOAL</label>
          <div class="input-container">
            <input 
              v-model.number="shipOpuHours" 
              type="number" 
              inputmode="numeric"
              placeholder="Hours"
              class="calculator-input"
            />
            <div class="result">{{ shipOpuGoal }}</div>
          </div>
        </div>
        
        <div class="calculator">
          <label class="calculator-label">SHIP & PACK GOAL</label>
          <div class="input-container">
            <input 
              v-model.number="shipPackHours" 
              type="number" 
              inputmode="numeric"
              placeholder="Hours"
              class="calculator-input"
            />
            <div class="result">{{ shipPackGoal }}</div>
          </div>
        </div>
        
        <div class="calculator">
          <label class="calculator-label">OPU & PACK GOAL</label>
          <div class="input-container">
            <input 
              v-model.number="opuPackHours" 
              type="number" 
              inputmode="numeric"
              placeholder="Hours"
              class="calculator-input"
            />
            <div class="result">{{ opuPackGoal }}</div>
          </div>
        </div>
      </div>
      
      <div class="version">v1.0.3</div>
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
  justify-content: space-between;
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

.calculators {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 15px;
  align-items: center;
  flex: 1;
}

.calculator {
  width: 100%;
  max-width: 350px;
  background-color: #f8f8f8;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.calculator-label {
  display: block;
  font-weight: bold;
  font-size: 16px;
  color: #cc0000;
  margin-bottom: 12px;
  text-align: center;
}

.input-container {
  display: flex;
  gap: 12px;
  align-items: center;
}

.calculator-input {
  flex: 1;
  padding: 12px;
  border: 2px solid #ddd;
  border-radius: 8px;
  font-size: 16px;
  text-align: center;
}

.calculator-input:focus {
  outline: none;
  border-color: #cc0000;
}

.result {
  flex: 1;
  padding: 12px;
  background-color: #cc0000;
  color: white;
  border-radius: 8px;
  font-size: 18px;
  font-weight: bold;
  text-align: center;
  min-height: 20px;
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
