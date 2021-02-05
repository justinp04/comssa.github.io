<template>
  <div class="mydiv">
    <h1>Meeting Minutes</h1>
    <ul>
      <li v-for="article of articles" :key="article.slug">
        <NuxtLink :to="`#${article.name}`">
          <div>
            <h2>{{ article.title }}</h2>
            <p>{{ article.description }}</p>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

// <script>
// import Minutes from '../components/Minutes.vue'

// export default {
//     components: {
//         Minutes,
//     },
// }
// </script>

<script>
  export default {
    async asyncData({ $content, params }) {
      const articles = await $content('minutes', params.slug)
        .only(['title'])
        .sortBy('createdAt', 'asc')
        .fetch()

      return {
        articles
      }
    }
  }
</script>

<style scoped>
.mydiv {
    /*These settings centre the content in mydiv on the component displayed */

    margin: auto;

    margin-top: 100px;

    width: 80%;
    max-width: 1400px;
}

/*Reference your own CSS file once you start working on this - 
You will need to use media queries to make it responsive  */
</style>