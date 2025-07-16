<script setup>
import { ref, watch, onMounted } from 'vue'

// Theme state
const isNight = ref(false)

// Toggle function
const toggleTheme = () => {
  isNight.value = !isNight.value
}

// Apply theme to body
watch(isNight, (value) => {
  document.body.className = value ? 'night' : 'day'
})

// On load
onMounted(() => {
  document.body.className = isNight.value ? 'night' : 'day'
})
</script>

<template>
  <div class="app">
<label class="theme-toggle">
  <input type="checkbox" v-model="isNight" />
  <span class="slider">
    <span class="emoji">{{ isNight ? '🌙' : '🌞' }}</span>
  </span>
</label>


    <router-view />
  </div>
</template>

<style scoped>
.theme-toggle {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 60px;
  height: 32px;
}

.theme-toggle input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: relative;
  display: block;
  width: 100%;
  height: 100%;
  background-color: #ddd;
  border-radius: 999px;
  transition: background-color 0.4s;
}

input:checked + .slider {
  background-color: #444;
}

/* Emoji moves like a toggle knob */
.emoji {
  position: absolute;
  left: 4px;
  top: 2px;
  width: 28px;
  height: 28px;
  font-size: 1.2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  border-radius: 50%;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease;
}

input:checked + .slider .emoji {
  transform: translateX(28px);
}

</style>
