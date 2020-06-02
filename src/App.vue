<template>
  <div id="app">
    <div class="post" v-for="post in posts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.description}}</p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      posts: []
    }
  },
  async mounted() {
   const res = await fetch('http://newsapi.org/v2/top-headlines?' +
          'sources=bbc-news&' +
          'apiKey=da9ac2bdfbcf4ccda4ec72394fd5cdb5');

          const posts = await res.json()
          this.posts = posts.articles;
  }
 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}

</style>
