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
      <div class="sm:hidden">
        123
      </div>
      <router-link
        class="icon-btn h-70px text-3xl leading-70px sm:flex-1"
        to="/"
        :title="t('header.home')"
      >
        {{ t('header.logo') }}
      </router-link>
      <nav class="<sm:hidden text-xl h-70px leading-70px">
        <router-link class="icon-btn mx-3" to="/" :title="t('header.home')">
          <carbon-home class="align-text-bottom mr-1" />
          {{ t('header.home') }}
        </router-link>
        <div class="icon-btn mx-3 group relative">
          <carbon-category class="align-text-bottom mr-1" />{{ t('header.category') }}
          <ul
            class="hidden group-hover:block absolute z-100 w-156px top-70px bg-gray-50 dark:bg-gray-800 bg-opacity-95 shadow-radiant"
          >
            <li
              v-for="item in [
                {
                  title: 'header.FE',
                  to: '/category/1',
                },
                {
                  title: 'header.Life',
                  to: '/category/1',
                },
              ]"
              :key="item.title"
              class="text-dark-100 hover:text-teal-600 hover:ml-10px transition-all duration-250 dark:text-gray-100 dark:hover:text-teal-600"
            >
              <router-link
                class="px-20px h-50px leading-50px"
                :to="item.to"
                :title="t(item.title)"
              >
                {{ t(item.title) }}
              </router-link>
            </li>
          </ul>
        </div>
        <router-link class="icon-btn mx-3" to="/" :title="t('header.Archive')">
          <carbon-dicom-overlay class="align-text-bottom mr-1" />
          {{ t('header.Archive') }}
        </router-link>
        <router-link class="icon-btn mx-2" to="/" :title="t('header.Website-link')">
          <carbon-link class="align-text-bottom" />
        </router-link>
        <router-link class="icon-btn mx-2" to="/about" :title="t('header.about')">
          <ant-design-heart-filled class="align-text-bottom" />
        </router-link>

        <header
          class="icon-btn mx-2 !outline-none"
          :title="t('header.toggle_dark')"
          @click="toggleDark()"
        >
          <carbon-moon v-if="isDark" class="align-text-bottom" />
          <carbon-sun v-else class="align-text-bottom" />
        </header>

        <a class="icon-btn mx-2" :title="t('header.toggle_langs')" @click="toggleLocales">
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
      </nav>
      <div class="h-70px pt-23px mx-2px">
        <carbon-search class="text-size-20px" />
      </div>
    </div>
  </header>
</template>
