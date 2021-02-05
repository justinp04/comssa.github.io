<template>
  <div class="mydiv">
    <article>
      <h1>{{ page.title }}</h1>
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