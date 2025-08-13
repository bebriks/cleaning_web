<!-- eslint-disable unicorn/prefer-query-selector -->
<script setup lang="ts">
  import { onMounted, ref } from 'vue'
  import { useDisplay } from 'vuetify'

  const { mobile } = useDisplay()
  const isScrolled = ref(false)
  const drawer = ref(false)

  const scrollToSection = (id: string) => {
    const element = document.getElementById(id)
    if (element) {
      element.scrollIntoView({
        behavior: 'smooth',
      })
    }
    drawer.value = false
  }

  onMounted(() => {
    window.addEventListener('scroll', () => {
      isScrolled.value = window.scrollY > 50
    })
  })
</script>

<template>
  <div :class="['header', { 'header-scrolled': isScrolled }]">
    <v-app-bar-nav-icon
      v-if="mobile"
      class="menu-icon"
      @click.stop="drawer = !drawer"
    />

    <ul v-if="!mobile" class="header-list">
      <li><a @click.prevent="() => scrollToSection('main')">ГЛАВНАЯ</a></li>
      <li><a @click.prevent="() => scrollToSection('services')">УСЛУГИ</a></li>
      <li><a @click.prevent="() => scrollToSection('works')">НАШИ РАБОТЫ</a></li>
      <li><a href="tel:+79221977132">+7 922 197-71-32</a></li>
    </ul>

    <v-navigation-drawer
      ref="app-bar"
      v-model="drawer"
      fixed
      right
      temporary
      width="250"
    >
      <v-list>
        <v-list-item class="arrow-left" @click="drawer = false">
          <v-icon icon="mdi-arrow-left" />
        </v-list-item>

        <v-list-item @click="() => scrollToSection('main')">
          <v-list-item-title>ГЛАВНАЯ</v-list-item-title>
        </v-list-item>

        <v-list-item @click="() => scrollToSection('services')">
          <v-list-item-title>УСЛУГИ</v-list-item-title>
        </v-list-item>

        <v-list-item @click="() => scrollToSection('works')">
          <v-list-item-title>НАШИ РАБОТЫ</v-list-item-title>
        </v-list-item>

        <v-list-item href="tel:+79221977132" @click="drawer = false">
          <v-list-item-title>+7 922 197-71-32</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<style lang="scss" scoped>
@use '../styles/settings';
.arrow-left {
  justify-self: end;
}
.header {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 1000;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 70px;
  background-color: settings.$app_bar_background;
}

.header-list {
  display: flex;
  list-style: none;
  width: 100%;
  max-width: 793px;
  justify-content: space-between;
  margin: 0 auto;
  padding: 0;

  li {
    padding: 0 15px;

    a {
      text-decoration: none;
      color: #000000;
      position: relative;
      padding-bottom: 5px;
      font-weight: 400;

      &:after {
        content: '';
        position: absolute;
        width: 0;
        height: 2px;
        bottom: 0;
        left: 0;
        background-color: #fff;
        transition: width 0.3s;
      }

      &:hover:after {
        width: 100%;
      }
    }
  }
}

.menu-icon {
  position: absolute;
  right: 20px;
  color: white !important;
}

// Стили для мобильного меню
.v-navigation-drawer {
  background-color: settings.$app_bar_background !important;

  .v-list-item {

    &--active {
      background-color: rgba(255, 255, 255, 0.1);
    }
  }
}

@media (max-width: 530px) {
  .header {
    justify-content: flex-start;
    padding-left: 20px;
  }

  .header-list {
    display: none;
  }
}
</style>
