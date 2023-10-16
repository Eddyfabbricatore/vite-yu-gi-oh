<script>
  export default {
    name: 'Header',
    props:{
      title: String
    }
  }
</script>

<template>
  <header class="d-flex justify-content-center align-items-center p-3">
    <img src="../assets/img/Yugioh-logo.webp" alt="Logo">

    <h1 class="m-0 ms-3">{{ title }}</h1>
  </header>
</template>

<style lang="scss" scoped>
  @use '../scss/partials/variables' as *;

  header{
    height: $h-header;
    background-color: $bg-header;

    img{
      width: $w-logo;
    }
  }
</style>