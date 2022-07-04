<template>
  <div>
    <div v-for="post of posts" :key="post.id">
      <div v-if="post.userId === userId">
        <h3>{{ post.title}}</h3>
        <p>{{ post.body}}</p>
        <small>{{ post.id}}</small>
      </div>
    </div>
  </div>
</template>

<script>
  import {getPosts} from '../services/postsService.js'

  export default {
  data(){
    return {
      posts : getPosts(),
      userId : Number,
    }
  },
  mounted(){
    this.userId = parseInt(this.$route.params.postsUser)
  }
  // props:{
  //   posts: {
  //     type:Array,
  //     userId:Number,
  //     id:Number,
  //     title:String,
  //     body:String,
  //     require:false,
  //     default() {
  //       return [{ title: 'no posts??' }]
  //     }
  //   },
  // },
  // methods:{
  //   savedPost(){
  //     getPosts()
  //   }
  // }
}
</script>

<style scoped>

</style>