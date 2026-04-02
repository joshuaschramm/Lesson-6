<script setup lang="ts">
defineProps<{
  label: string
  url: string
  icon: string
  colorClass: string
  isDark: boolean
}>()
</script>

<template>
  <a
    :href="url"
    target="_blank"
    rel="noopener noreferrer"
    :class="['custom-link-btn', colorClass, { 'dark-btn': isDark }]"
  >
    <i :class="'mdi ' + icon + ' btn-icon'"></i>
    <span>{{ label }}</span>
  </a>
</template>

<style scoped>
.custom-link-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  height: 56px;
  color: #fff;
  font-weight: 700;
  font-size: 1.1rem;
  border-radius: 8px;
  text-decoration: none;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  cursor: pointer;
  position: relative;
  overflow: hidden;
  background-size: 200% 100%;
  background-position: 100% 0;
  transition: background-position 0.4s ease, color 0.4s ease, transform 0.3s ease, box-shadow 0.3s ease;
}

.hover-magenta {
  background-image: linear-gradient(to right, #E6007E 50%, #000 50%);
}

.hover-cyan {
  background-image: linear-gradient(to right, #00B5E2 50%, #000 50%);
}

.hover-yellow {
  background-image: linear-gradient(to right, #FFED00 50%, #000 50%);
}

/* Dark mode button backgrounds */
.dark-btn.hover-magenta {
  background-image: linear-gradient(to right, #E6007E 50%, #222 50%);
}

.dark-btn.hover-cyan {
  background-image: linear-gradient(to right, #00B5E2 50%, #222 50%);
}

.dark-btn.hover-yellow {
  background-image: linear-gradient(to right, #FFED00 50%, #222 50%);
}

.custom-link-btn:hover {
  background-position: 0 0;
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.2);
}

.hover-yellow:hover {
  color: #000;
}

.hover-yellow:hover .btn-icon {
  color: #000;
}

.custom-link-btn:active {
  transform: translateY(0);
}

.btn-icon {
  color: #fff;
  font-size: 22px;
  transition: color 0.4s ease;
}
</style>
