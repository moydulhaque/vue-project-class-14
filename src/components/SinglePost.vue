<template>
  <li>
    <div
        style="display: inline-block"
        :class="{ 'fav' : post.fav }"
    >{{ post.title }}</div> |
    <button class="border rounded-md bg-gray-200 text-black p-2" @click="handleClick(post)">Delete Post</button> |
    <button class="border rounded-md bg-gray-200 text-black p-2" @click="$emit('fav', post)">Fav Post</button>
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