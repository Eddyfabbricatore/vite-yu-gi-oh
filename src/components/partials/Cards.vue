<script>
  export default {
    name: 'Cards',
    props:{
      name: String,
      archetype: String,
      imgSrc: String
    }
  }
</script>

<template>
  <div class="col mb-3">
    <div class="card text-center">
      <img :src="imgSrc" :alt="name">

      <div class="card-text rounded-bottom">
        <h4 class="my-3">{{ name }}</h4>

        <p>{{ archetype }}</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @use '../../scss/partials/variables' as *;

  .col{
    width: $w-col;

    .card-text{
      height: $h-card-text;
      background-color: $bg-body;

      h4{
        color: $card-title;
      }
    }
  }
</style>