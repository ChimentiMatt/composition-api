<template>
  <div class="home"> 
    <h1>Home</h1>
    <PostList :posts="posts"/>
  </div>
</template>

<script>
import PostList from './components/PostList.vue'
import { ref } from 'vue'

export default {
  name: 'Home',
  components: { PostList },
  setup() {
    const posts = ref([
      { title: 'Welcome to the blog', body: 'Lorem ipsum', id: 1},
      { title: 'top 5 CSS tips', body: 'Lorem ipsum', id: 2}
    ])

    return { posts }
  }
}
</script>

<style scoped>

</style>
