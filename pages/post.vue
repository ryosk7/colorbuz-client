<template>
  <div>
    <li v-for="post in posts" :key="post.id">
      <p>hoge</p>
    </li>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [],
      newPost: ''
    }
  },
  mounted() {
    this.fetchPosts()
  },
  methods: {
    fetchPosts() {
      this.$axios.get('/posts').then(
        (response) => {
          for (let i = 0; i < response.data.posts.length; i++) {
            this.posts.push(response.data.posts[i])
          }
        },
        (error) => {
          console.log(error)
        }
      )
    }
  }
}
</script>
