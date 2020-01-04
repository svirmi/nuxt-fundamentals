<template>
<nav class="nav">
  <div class="logo">
      <nuxt-link class="logo text-lg" :to="{name: 'index'}">Nuxt basis</nuxt-link>

      <span class="subheader">Some text here</span>
  </div>
</nav>
</template>

<script>
    export default {
        name: "NavBar"
    }
</script>

<style scoped>

</style>
