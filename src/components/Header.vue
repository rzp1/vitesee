<script setup lang="ts">
import { isDark, toggleDark } from '~/composables'

const { t, availableLocales, locale } = useI18n()

const toggleLocales = () => {
  // change to some real logic
  const locales = availableLocales
  locale.value = locales[(locales.indexOf(locale.value) + 1) % locales.length]
}
</script>

<template>
  <header
    class="text-14px sticky top-0 h-70px w-full bg-gray-50 dark:bg-gray-800 bg-opacity-95 shadow-sm"
  >
    <div class="max-w-1080px m-auto flex justify-between text-gray-700 dark:text-gray-200">
      <router-link
        class="icon-btn h-70px text-3xl leading-70px"
        to="/"
        :title="t('button.home')"
      >
        {{ t('header.logo') }}
      </router-link>
      <div class="nav-collapse" />
      <nav class="text-xl h-70px leading-70px">
        <router-link class="icon-btn mx-3" to="/" :title="t('button.home')">
          <carbon-home class="align-text-bottom mr-1" />
          {{ t('button.home') }}
        </router-link>
        <div class="icon-btn mx-3 group relative">
          <carbon-category class="align-text-bottom mr-1" />分类
          <ul
            class="hidden group-hover:block absolute z-100 w-156px top-70px bg-gray-50 dark:bg-gray-800 bg-opacity-95 shadow-radiant"
          >
            <li
              v-for="item in [`FE`, `Life`]"
              :key="item"
              class="text-dark-100 hover:text-teal-600 hover:ml-10px transition-all duration-250 dark:text-gray-100 dark:hover:text-teal-600"
            >
              <router-link class="px-20px h-50px leading-50px" to="/category/1">
                {{ item }}
              </router-link>
            </li>
          </ul>
        </div>
        <router-link class="icon-btn mx-3" to="/" :title="t('button.home')">
          <carbon-dicom-overlay class="align-text-bottom mr-1" />存档
        </router-link>
        <router-link class="icon-btn mx-3" to="/" :title="t('button.home')">
          <carbon-link class="align-text-bottom mr-1" />友链
        </router-link>
        <router-link class="icon-btn mx-3" to="/about" :title="t('button.home')">
          <ant-design-heart-filled class="align-text-bottom mr-1" />关于
        </router-link>

        <button
          class="icon-btn mx-2 !outline-none"
          :title="t('button.toggle_dark')"
          @click="toggleDark()"
        >
          <carbon-moon v-if="isDark" class="align-text-bottom" />
          <carbon-sun v-else class="align-text-bottom" />
        </button>

        <a class="icon-btn mx-2" :title="t('button.toggle_langs')" @click="toggleLocales">
          <carbon-language class="align-text-bottom" />
        </a>

        <a
          class="icon-btn mx-2"
          rel="noreferrer"
          href="https://github.com/rzp1"
          target="_blank"
          title="GitHub"
        >
          <carbon-logo-github class="align-text-bottom" />
        </a>
        <carbon-search class="icon-btn mx-2 align-text-bottom" />
      </nav>
    </div>
  </header>
</template>
