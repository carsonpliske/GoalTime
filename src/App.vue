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
        <div class="target-logo"></div>
      </div>
      
      <div class="calculators">
        <div class="calculator">
          <label class="calculator-label">OPU UNIT GOAL</label>
          <div class="input-container">
            <input 
              v-model.number="opuHours" 
              type="number" 
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
              placeholder="Hours"
              class="calculator-input"
            />
            <div class="result">{{ opuPackGoal }}</div>
          </div>
        </div>
      </div>
      
      <div class="version">v1.0.2</div>
    </div>
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
  width: 100vw;
  background-color: white;
  margin: 0;
  padding: 0;
  overflow-y: auto;
  position: fixed;
  top: 0;
  left: 0;
}

.content-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  padding: 0 20px;
}

.logo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 30px;
  margin-bottom: 20px;
}

.target-logo {
  width: 120px;
  height: 120px;
  background-color: #cc0000;
  border-radius: 50%;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.target-logo::before {
  content: '';
  width: 72px;
  height: 72px;
  background-color: white;
  border-radius: 50%;
  position: absolute;
}

.target-logo::after {
  content: '';
  width: 24px;
  height: 24px;
  background-color: #cc0000;
  border-radius: 50%;
  position: absolute;
  z-index: 1;
}

.calculators {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
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
