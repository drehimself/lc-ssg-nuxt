<template>
  <div class="markdown-body">
    <h2>{{ postInMarkdown.title }}</h2>
    <p>By: {{ postInMarkdown.author }}</p>
    <nuxt-content :document="postInMarkdown" />
  </div>
</template>

<script>
import Logo from '~/components/Logo'
import 'github-markdown-css/github-markdown.css'

export default {
  components: {
    Logo,
  },
  async asyncData({ $content, params }) {
    const postInMarkdown = await $content(params.slug)
      .fetch()
      .catch(err => {
        console.log(err)
      })

    return {
      postInMarkdown
    }
  }
}
</script>

<style>
.markdown-body {
		box-sizing: border-box;
		min-width: 200px;
		max-width: 980px;
		margin: 0 auto;
		padding: 45px;
	}

	@media (max-width: 767px) {
		.markdown-body {
			padding: 15px;
		}
	}
</style>
