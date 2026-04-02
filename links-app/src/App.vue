<script setup lang="ts">
interface Link {
  label: string
  url: string
}

const links: Link[] = [
  { label: 'Portfolio', url: 'https://www.behance.net/joshuaschramm' },
  { label: 'LinkedIn', url: 'https://www.linkedin.com/in/joshuaschramm/' },
  { label: 'Email', url: 'mailto:josh@joshschramm.com' }
]
</script>

<template>
  <div class="app-container">
    <div class="card">
      <!-- Profile Section -->
      <div class="profile-section">
        <div class="profile-pic-wrapper">
          <img
            src="https://media.licdn.com/dms/image/v2/C4D03AQE33QcZRqe6Nw/profile-displayphoto-shrink_400_400/profile-displayphoto-shrink_400_400/0/1616509027708?e=1776902400&v=beta&t=-K-4z9MXOyFBiDaGYUBIH2JRbviKtEJKw8BrlBz0o5s"
            alt="Joshua Schramm"
            class="profile-pic"
          />
        </div>
        <h1 class="name">JOSHUA SCHRAMM</h1>
        <p class="bio">Creative Designer & Illustrator</p>
      </div>

      <!-- Links Section -->
      <div class="links-section">
        <a
          v-for="link in links"
          :key="link.label"
          :href="link.url"
          target="_blank"
          rel="noopener noreferrer"
          class="link-button"
        >
          {{ link.label }}
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.app-container {
  width: 100%;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  background: url('@/assets/Background.jpg') center/cover fixed;
  background-color: #f5f5f5;
}

.card {
  width: 100%;
  max-width: 480px;
  background: white;
  border-radius: 8px;
  padding: 48px 32px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15);
}

.profile-section {
  text-align: center;
  margin-bottom: 40px;
}

.profile-pic-wrapper {
  margin-bottom: 24px;
  position: relative;
  display: inline-block;
}

.profile-pic {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  display: block;
  border: 3px solid #000000;
  box-shadow:
    3px 3px 0 #00B5E2,
    -2px -2px 0 #E6007E;
}

/* CMYK Offset Effect wrapper */
.profile-pic-wrapper::before {
  content: '';
  position: absolute;
  width: 120px;
  height: 120px;
  border-radius: 50%;
  top: 3px;
  left: 3px;
  border: 2px solid #FFED00;
  opacity: 0.5;
  pointer-events: none;
}

.profile-pic-wrapper::after {
  content: '';
  position: absolute;
  width: 120px;
  height: 120px;
  border-radius: 50%;
  top: -2px;
  left: -2px;
  border: 2px solid #00B5E2;
  opacity: 0.4;
  pointer-events: none;
}

.name {
  font-size: 32px;
  font-weight: 900;
  color: #000000;
  margin: 0 0 8px 0;
  letter-spacing: 0.05em;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
  position: relative;
  text-transform: uppercase;
  line-height: 1;
  text-shadow:
    3px 3px 0 #00B5E2,
    -3px -3px 0 #E6007E,
    4px -4px 0 #FFED00,
    2px -2px 0 #00B5E2,
    -2px 2px 0 #E6007E;
}


.bio {
  font-size: 16px;
  color: #333333;
  margin: 0;
  line-height: 1.6;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
}

.links-section {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.link-button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  padding: 16px 24px;
  background: #000000;
  color: white;
  text-decoration: none;
  font-weight: 600;
  font-size: 16px;
  border-radius: 6px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
  letter-spacing: 0.5px;
}

.link-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, #00B5E2, #E6007E, #FFED00);
  transition: left 0.3s ease;
  z-index: -1;
}

.link-button:nth-child(1)::before {
  background: #00B5E2;
}

.link-button:nth-child(2)::before {
  background: #E6007E;
}

.link-button:nth-child(3)::before {
  background: #FFED00;
}

.link-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.link-button:nth-child(3):hover {
  color: #000000;
}

.link-button:hover::before {
  left: 0;
}

.link-button:active {
  transform: translateY(0);
}

/* Mobile responsiveness */
@media (max-width: 480px) {
  .card {
    padding: 32px 24px;
  }

  .name {
    font-size: 24px;
  }

  .bio {
    font-size: 14px;
  }

  .profile-pic {
    width: 100px;
    height: 100px;
  }

  .profile-pic-wrapper::before,
  .profile-pic-wrapper::after {
    width: 100px;
    height: 100px;
  }
}
</style>
