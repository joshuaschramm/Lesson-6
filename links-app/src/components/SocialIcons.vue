<script setup lang="ts">
defineProps<{
  isDark: boolean
}>()

const socials = [
  { name: 'Instagram', icon: 'mdi-instagram', url: 'https://www.instagram.com/joshuaschramm/' },
  { name: 'Facebook', icon: 'mdi-facebook', url: 'https://www.facebook.com/joshuaschramm' },
  { name: 'Behance', icon: 'mdi-palette', url: 'https://www.behance.net/joshuaschramm' },
  { name: 'Bluesky', icon: 'mdi-cloud', url: 'https://bsky.app/profile/joshuaschramm' }
]
</script>

<template>
  <div class="social-row">
    <a
      v-for="social in socials"
      :key="social.name"
      :href="social.url"
      target="_blank"
      rel="noopener noreferrer"
      :class="['social-icon', { 'social-icon-dark': isDark }]"
      :aria-label="social.name"
      :title="social.name"
    >
      <i :class="'mdi ' + social.icon"></i>
    </a>
  </div>
</template>

<style scoped>
.social-row {
  display: flex;
  justify-content: center;
  gap: 16px;
  margin-top: 24px;
}

.social-icon {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  color: #333;
  background: transparent;
  border: 2px solid #ccc;
  font-size: 22px;
  transition: all 0.3s ease;
}

.social-icon:hover {
  color: #fff;
  background: #000;
  border-color: #000;
  transform: translateY(-2px);
}

.social-icon-dark {
  color: #aaa;
  border-color: #555;
}

.social-icon-dark:hover {
  color: #fff;
  background: #E6007E;
  border-color: #E6007E;
}
</style>
