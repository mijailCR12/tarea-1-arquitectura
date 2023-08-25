<style>
  h1 {
   padding-top: 20px;
  }
</style>
<script>
  export default {
    async asyncData({ $content, params }) {
      const articles = await $content('articles')
        .only(['title','description', 'slug'])
        .sortBy('createdAt', 'asc')
        .fetch()
      return {
        articles
      }
    }
  }
</script>

<template>
  <!-- <nuxt-img provider="random" src="../static/images/favicon.png" width="300" height="169" /> -->
  <div class="container">
   <div class="row">
    <h1>Turismo en Costa Rica</h1>
	<!-- <NuxtLink to="/search">Search page</NuxtLink> -->
    <ul style="list-style: none;">
      <li v-for="article of articles" :key="article.slug">
        <NuxtLink style="text-decoration:none" :to="{ name: 'blog-slug', params: { slug: article.slug } }" no-rel>
          <div>
            <h2>{{ article.title }}</h2><h4 style="color: black;" >{{article.description}}</h4>
          </div>
        </NuxtLink>
      </li>
    </ul>
   </div>
  </div>
</template>