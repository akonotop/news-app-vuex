<template>
  <div id="app">
    <div class="post" v-for="post in allPosts" :key="post.id" @click="navTo(post.url)">
      <img :src="post.urlToImage" />
      <!-- v-if="article.urlToImage" :src="article.urlToImage" alt="" -->
      <h2>{{post.title}}</h2>
      <p>{{post.description}}</p>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
export default {
  name: 'App',
  computed: mapGetters(['allPosts']),
  methods: mapActions(['fetchPosts']), 
      navTo(url) {
        window.open(url);
      },    
      async mounted() {
      this.fetchPosts();
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

img {
  width: 400px;
}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}

</style>
