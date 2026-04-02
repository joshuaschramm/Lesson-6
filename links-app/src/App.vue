<script setup lang="ts">
import { ref } from 'vue'
import { useTheme } from 'vuetify'
import ProfileAvatar from './components/ProfileAvatar.vue'
import LinkButton from './components/LinkButton.vue'
import ThemeToggle from './components/ThemeToggle.vue'
import ProfileCard from './components/ProfileCard.vue'
import SocialIcons from './components/SocialIcons.vue'

const links = [
  { label: 'Portfolio', url: 'https://www.behance.net/joshuaschramm', icon: 'mdi-briefcase', colorClass: 'hover-magenta' },
  { label: 'LinkedIn', url: 'https://www.linkedin.com/in/joshuaschramm/', icon: 'mdi-linkedin', colorClass: 'hover-cyan' },
  { label: 'Email', url: 'mailto:josh@joshschramm.com', icon: 'mdi-email', colorClass: 'hover-yellow' }
]

const profileImage = 'https://media.licdn.com/dms/image/v2/C4D03AQE33QcZRqe6Nw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1616509027708?e=1776902400&v=beta&t=3r6Sxa77orp3yLJ4EhePKCEIXlHrkBGQ2RN8WDmjHAE'

const theme = useTheme()
const isDark = ref(theme.global.current.value.dark)
function toggleTheme() {
  theme.global.name.value = isDark.value ? 'light' : 'dark'
  isDark.value = !isDark.value
}
</script>

<template>
  <v-app>
    <v-main :class="['custom-main-bg', { 'main-dark': isDark }]">
      <ThemeToggle :isDark="isDark" @toggle="toggleTheme" />

      <ProfileCard :isDark="isDark">
        <ProfileAvatar :src="profileImage" alt="Joshua Schramm" />

        <h1 class="custom-name">JOSHUA SCHRAMM</h1>
        <p class="custom-bio">Creative Designer &amp; Illustrator</p>

        <div class="button-stack">
          <LinkButton
            v-for="link in links"
            :key="link.label"
            :label="link.label"
            :url="link.url"
            :icon="link.icon"
            :colorClass="link.colorClass"
            :isDark="isDark"
          />
        </div>

        <SocialIcons :isDark="isDark" />
      </ProfileCard>
    </v-main>
  </v-app>
</template>

<style scoped>
.custom-main-bg {
  min-height: 100vh;
  background: url('@/assets/Background.jpg') center/cover fixed;
  background-color: #f5f5f5;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 24px;
  transition: background 0.4s ease;
}

.main-dark {
  background: url('@/assets/Background-dark.jpg') center/cover fixed;
  background-color: #111;
}

.custom-name {
  font-size: 2rem;
  font-weight: 900;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin: 0 0 8px 0;
  text-align: center;
  color: #000;
  text-shadow: 3px 3px 0 #00B5E2, -3px -3px 0 #E6007E, 2px -2px 0 #00B5E2, -2px 2px 0 #E6007E;
}

.custom-bio {
  font-size: 1.1rem;
  color: #555;
  text-align: center;
  margin: 0 0 28px 0;
}

.button-stack {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

@media (max-width: 480px) {
  .custom-name {
    font-size: 1.3rem;
  }
  .custom-bio {
    font-size: 1rem;
  }
}

/* Dark mode text overrides (slotted inside ProfileCard) */
:deep(.dark-mode) .custom-name {
  color: #fff;
}

:deep(.dark-mode) .custom-bio {
  color: #aaa;
}
</style>


