<template>
  <div class="minutes">
    <h1>{{ page.title }}</h1>
    <article>
      <nuxt-content :document="page" />
    </article>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const page = await $content('minutes', params.minute, 'index').fetch()

    return {
      page
    }
  }
}
</script>

<style scoped>
@import '~/assets/css/minutes.css';
</style>
