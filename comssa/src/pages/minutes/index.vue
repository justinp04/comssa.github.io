<template>
  <div class="minutes">
    <h1>Meeting Minutes</h1>
    <ul>
      <li v-for="article of articles" :key="article.slug">
        <NuxtLink :to="article.slug" append>
          <div>
            <h2>{{ article.title }}</h2>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      const articles = await $content('minutes', params.slug)
        .only(['title', 'slug', 'author'])
        .sortBy('createdAt', 'asc')
        .fetch()

      return {
        articles
      }
    }
  }
</script>

<style scoped>
@import '~/assets/css/minutes.css';
</style>
