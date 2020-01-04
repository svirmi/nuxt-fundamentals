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
        <a :href="`/posts/${related.id}`">{{related.title}}</a>
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

          posts: [
            {
              id: 'post-1',
              title: 'post one title',
              content: 'post one content',
            },
            {
              id: 'two',
              title: 'post TWO title',
              content: 'post TWO content',
            },
            {
              id: 'post-3',
              title: 'post 3 title',
              content: 'post 3 content',
            },
            {
              id: 'four',
              title: 'post 4 title',
              content: 'post 4 content',
            }
          ]
        }
      },
      computed: {
        post() {
          return this.posts.find(post => post.id === this.id)
        },
        relatedPosts() {
          return this.posts.filter(post => post.id !== this.id)
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

