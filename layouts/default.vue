<template>
  <div class="bg-gray-300">
    <div class="bg-gray-300 fixed top-0 w-full">
      <CommonHeader />
    </div>
    <main>
      <Nuxt />
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      theme: 'light',
      dark: true,
    }
  },
  created() {
    this.$store.dispatch('getRelease')
  },
  mounted() {
    if (
      localStorage.theme === 'dark' ||
      (!('theme' in localStorage) &&
        window.matchMedia('(prefers-color-scheme: dark)').matches)
    ) {
      document.documentElement.classList.add('dark')
      this.theme = 'dark'
      this.dark = true
    } else {
      document.documentElement.classList.remove('dark')
      this.theme = 'light'
      this.dark = false
    }
    // document.addEventListener('touchmove', this.handleTouchMove, {
    //   passive: false,
    // })
  },
  methods: {
    // handleTouchMove(event) {
    //   event.preventDefault()
    // },
  },
}
</script>
<style lang="postcss" scoped>
._theme-color {
  @apply bg-black;
}
</style>
