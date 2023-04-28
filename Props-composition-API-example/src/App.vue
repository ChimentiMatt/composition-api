<template>
  <div class="home"> 
    <h1>Home</h1>
    <PostList :posts="posts"/>
    <!-- <p>{{ posts2 }}</p> -->
  </div>
</template>

<script>
import PostList from './components/PostList.vue'
import getPosts from './composables/getPosts.js'

import { ref } from 'vue'

export default {
  name: 'Home',
  components: { PostList },
  setup() {
    const { posts2, error, load} = getPosts();
    console.log(posts2)

    const posts = ref([
      { title: 'Welcome to the blog', body: 'Lorem ipsum', id: 1},
      { title: 'top 5 CSS tips', body: 'Lorem ipsum', id: 2}
    ])

    return { posts , posts2}
  }
}
</script>

<style scoped>

</style>
