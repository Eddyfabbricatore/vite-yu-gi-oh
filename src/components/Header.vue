<script>
export default {
  name: 'Header',
  props:{
    title: String
  }
}
</script>

<template>
  <header class="text-center mt-3">
    <h1>{{ title }}</h1>
  </header>
</template>

<style lang="scss" scoped>

</style>