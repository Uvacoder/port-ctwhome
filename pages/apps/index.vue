<template>
  <div class="flex flex-col px-4">
    <div class="container mx-auto h-full">
      <blog-list :posts="posts" more-button="View more Articles" class="mt-20" />
    </div>
    <footer-main class="mt-30" />
  </div>
</template>

<script>
export default {
  transition: 'fade',
  async asyncData ({ $content, params }) {
    // blog list
    const posts = await $content('apps')
      .sortBy('created', 'desc')
      .fetch()
    return {
      posts
    }
  },
  methods: {
    formatDate (date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    }
  }
}
</script>

<style scoped>

</style>
