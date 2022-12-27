<template>
  <div class="mt-5 mb-5 p-2">
    <button class="border rounded-md bg-orange-600 text-white p-2" @click="addPost">Add Post</button>

  </div>
  
<!--  fav count: {{ favCount }}<br>-->
<!--  Un Fav Count: {{ unFavCount}}-->
<div class="mt-5 mb-5 p-2">  
<h1 class="text-2xl mb-2 underline">All Posts</h1>
  <ul>
    <single-post
        style="margin-bottom: 10px"
        v-for="(post, index) in posts"
        :key="index"
        :post="post"
        @delete="handleDelete"
        @fav="handleFav"
    />
  </ul>
  <br>
  <h1 class="text-2xl mb-2 underline">Favs</h1>
  <ul>
    <single-post
        style="margin-bottom: 10px"
        v-for="(post, index) in favs"
        :key="index"
        :post="post"
        @delete="handleDelete"
        @fav="handleFav"
    />
  </ul>
  <br>
  <h1 class="text-2xl mb-2 underline">UnFavs</h1>
  <ul>
    <single-post
        style="margin-bottom: 10px"
        v-for="(post, index) in unFavs"
        :key="index"
        :post="post"
        @delete="handleDelete"
        @fav="handleFav"
    />
  </ul>
</div>
</template>

<script>
import SinglePost from "../components/SinglePost.vue";

export default {
  name: "HomePage",
  components: {SinglePost},
  data() {
    return {
      message: "Hello Bangladesh",
      posts: [
        {
          id: 1,
          title: "Post 1",
          fav: true
        },
        {
          id: 2,
          title: "Post 2",
          fav: false
        },
        {
          id: 3,
          title: "Post 3",
          fav: true
        }
      ],
    }
  },
  computed: {
    favs() {
      return this.posts.filter(post => post.fav)
    },
    unFavs() {
      return this.posts.filter(post => !post.fav)
    },
  },
  methods: {
    handleDelete(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    addPost() {
      this.posts.push({
        id: this.posts.length + 1,
        title: `Post ${this.posts.length + 1}`
      })
    },
    handleFav(post) {
      this.posts = this.posts.map(p => {
        if (p.id === post.id) {
          p.fav = !p.fav
        }
        return p
      })
    }
  }

}
</script>

<style scoped>
h1 {
  color: rgb(4, 55, 142);
}
</style>