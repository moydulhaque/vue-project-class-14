<template>
  <li>
    <div
        style="display: inline-block"
        :class="{ 'fav' : post.fav }"
    >{{ post.title }}</div> |
    <button @click="handleClick(post)">Delete Post</button> |
    <button @click="$emit('fav', post)">Fav Post</button>
  </li>
</template>

<script>
export default {
  name: "SinglePost",
  props: ['post'],
  methods: {
    handleClick(post) {
      this.$emit('delete', post)
    }
  }
}
</script>

<style scoped>
.fav {
  color: green;
}
</style>