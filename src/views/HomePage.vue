<template>
  <button @click="addPost">Add Post</button>
  <br>
<!--  fav count: {{ favCount }}<br>-->
<!--  Un Fav Count: {{ unFavCount}}-->
  <h1>All</h1>
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
  <h1>Favs</h1>
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
  <h1>UnFavs</h1>
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
  color: green;
}
</style>