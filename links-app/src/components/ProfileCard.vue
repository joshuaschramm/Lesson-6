<script setup lang="ts">
defineProps<{
  isDark: boolean
}>()
</script>

<template>
  <div :class="['custom-card', { 'dark-mode': isDark }]">
    <slot />
  </div>
</template>

<style scoped>
.custom-card {
  max-width: 480px;
  width: 100%;
  background: #ffffff;
  border-radius: 16px;
  padding: 48px 32px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15);
  text-align: center;
}

.dark-mode {
  background: #1a1a1a !important;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
}

@media (max-width: 480px) {
  .custom-card {
    padding: 32px 16px;
  }
}
</style>
