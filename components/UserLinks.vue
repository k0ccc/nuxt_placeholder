<template>
  <div v-if="users.length">
    <div v-for="user of users" :key="user">
      <NuxtLink :to="`/${user}`">Пользователь под номером: {{user}}</NuxtLink>
    </div>
  </div>
</template>

<script>
  import {savePosts} from '../services/postsService.js'

  export default {

  data() {
    return {
      users: [],
    }
  },
  async beforeCreate() {
    // get all posts
    const i = await fetch("https://jsonplaceholder.typicode.com/posts")
    this.posts = await i.json();
    savePosts(this.posts)
    // get unique users
    const numberArr = [];
    for (const i in this.posts) {
      numberArr.push(this.posts[i].userId);
    }
    this.users = [...new Set(numberArr)];
  }
}
</script>

<style scoped>

</style>