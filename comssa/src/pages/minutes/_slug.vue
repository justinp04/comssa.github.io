<template>
  <div class="minutes">
    <article>
      <nuxt-content :document="page" />
    </article>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const page = await $content('minutes', params.slug).fetch()

    return {
      page
    }
  }
}
</script>

<style scoped>
@import '~/assets/css/minutes.css';
</style>
