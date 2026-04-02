<script setup lang="ts">
defineProps<{
  isDark: boolean
}>()

defineEmits<{
  toggle: []
}>()
</script>

<template>
  <button
    :class="['theme-toggle', { 'theme-toggle-dark': isDark }]"
    @click="$emit('toggle')"
    :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'"
  >
    <i :class="'mdi ' + (isDark ? 'mdi-white-balance-sunny' : 'mdi-moon-waning-crescent') + ' toggle-icon' + (isDark ? ' toggle-icon-dark' : '')"></i>
  </button>
</template>

<style scoped>
.theme-toggle {
  position: fixed;
  top: 20px;
  right: 20px;
  z-index: 100;
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(8px);
  border: 2px solid #ccc;
  border-radius: 50%;
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
}

.theme-toggle:hover {
  border-color: #00B5E2;
  transform: rotate(20deg);
}

.toggle-icon {
  font-size: 22px;
  color: #333;
  transition: color 0.3s ease;
}

.theme-toggle-dark {
  border-color: #555;
  background: rgba(30, 30, 30, 0.8) !important;
}

.toggle-icon-dark {
  color: #FFED00 !important;
}
</style>
