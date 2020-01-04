<template>
<div class="container">

  <article>
    <h1 class="title">{{post.title}}</h1>
    <p>{{post.content}}</p>
  </article>

  <aside>
    <h3>Posts you might alos like:</h3>
    <ul>
      <li v-for="related in relatedPosts">
        <nuxt-link :to="{name: 'posts-id', params: {id: related.id}}">{{related.title}}</nuxt-link>
      </li>
    </ul>
  </aside>

</div>
</template>

<script>
    export default {
      name: "post",
      data() {
        return {
          id: this.$route.params.id,
        }
      },
      computed: {
        post() {
          return this.$store.state.posts.all.find(post => post.id === this.id)
        },
        relatedPosts() {
          return this.$store.state.posts.all.filter(post => post.id !== this.id)
        }
      }
    }
</script>

<style scoped>
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .title {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
  }

  .subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
  }
</style>

