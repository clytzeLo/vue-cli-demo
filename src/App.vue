<template>
  <div class="app">
    hello App
  </div>
</template>

<script>
export default {
  name: 'App',
  mounted() {
    console.log(process.env, 'p');
  }
}
</script>

<style lang="scss" scoped>
.app {
  color: skyblue
}
</style>