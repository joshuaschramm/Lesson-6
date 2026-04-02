<script setup lang="ts">
defineProps<{
  src: string
  alt: string
}>()
</script>

<template>
  <div class="avatar-section">
    <div class="custom-avatar-wrapper">
      <img :src="src" :alt="alt" class="avatar-img" />
      <div class="avatar-ring avatar-cyan"></div>
      <div class="avatar-ring avatar-magenta"></div>
    </div>
  </div>
</template>

<style scoped>
.avatar-section {
  display: flex;
  justify-content: center;
  margin-bottom: 24px;
}

.custom-avatar-wrapper {
  position: relative;
  width: 120px;
  height: 120px;
}

.avatar-img {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  position: relative;
  z-index: 1;
}

.avatar-ring {
  position: absolute;
  width: 120px;
  height: 120px;
  border-radius: 50%;
  pointer-events: none;
  z-index: 0;
}

.avatar-cyan {
  border: 2px solid #00B5E2;
  top: 4px;
  left: 4px;
  opacity: 0.5;
}

.avatar-magenta {
  border: 2px solid #E6007E;
  top: -4px;
  left: -4px;
  opacity: 0.5;
}

@media (max-width: 480px) {
  .custom-avatar-wrapper,
  .avatar-img,
  .avatar-ring {
    width: 100px;
    height: 100px;
  }
}
</style>
