<template>
  <div>
    <h3>Blog Posts</h3>
    <ul>
      <li v-for="(post, index) in posts" :key="index">
        <NuxtLink :to="`/posts/${post.slug}`">{{ post.title }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: null
    }
  },
  async fetch() {
    this.posts = await this.$content()
      .fetch()
  }
}
</script>

<style>

</style>
