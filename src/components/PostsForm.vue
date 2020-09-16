<template>
  <div>
    <form @submit.prevent='onSubmit'>
      <label for="title">Title</label>
      <input type="text" name="" id="title" v-model='title'>
      <label for="body">Desc</label>
      <input type="text" name="" id="body" v-model='body'>
      <button type="submit">Create Post</button>
    </form>
    <hr>
  </div>
</template>

<script>
import {mapMutations} from 'vuex'
export default {
  data() {
    return {
      title: '',
      body: '',
    }
  },
  methods: {
    ...mapMutations(['newPost']),
    onSubmit() {
      this.newPost({
        title: this.title,
        body: this.body,
      })
      this.title = this.body = ''
    },
  }
}
</script>

<style>
  form {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 400px;
    border: 1px solid #000;
    border-radius: 10px;
    margin: 0 auto 25px;
    padding: 15px 0;
  }
  label {
    margin: 0 0 5px 0;
  }
  input {
    display: block;
    width: 50%;
    margin: 0 0 10px 0;
  }
</style>