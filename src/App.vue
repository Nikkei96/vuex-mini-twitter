<template>
  <div id="app">
    <PostsForm />
    <h3>Общее кол-во постов: {{postsCount}}</h3>
    <div class="post" v-for='post of validPosts' :key='post.id'>
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import PostsForm from '@/components/PostsForm'
export default {
  name: 'App',
  computed: mapGetters(['validPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  mounted() {
    // this.$store.dispatch('fetchPosts')
    this.fetchPosts(7)
  },
  components: {
    PostsForm,
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
  width: 600px;
}

.post{
  border: 1px solid #000;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 10px;
  margin: 0 0 10px 0;
}
</style>
