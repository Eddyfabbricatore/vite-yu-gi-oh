<script>
  import axios from 'axios';
  import { store } from '../data/store';
  import Cards from './partials/Cards.vue';

  export default {
    name: 'Main',
    components:{
      Cards
    },

    data(){
      return{
        store
      }
    }
  }
</script>

<template>
  <main>
    <div class="container my-5">
      <div class="row p-5">
        <div class="found p-3">
          <p class="m-0" v-if="store.list.length > 0">Founds {{ store.list.length }} cards</p>
          <p class="m-0" v-else>Nessun risultato trovato</p>
        </div>

        <Cards
          v-for="card in store.list"
          :key="card.id" 
          :name="card.name"
          :archetype="card.archetype"
          :imgSrc="card.card_images[0].image_url" />
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
  @use '../scss/partials/variables' as *;

  main{
    .row{
      background-color: $bg-header;

      .found{
        background-color: $bg-found;

        p{
          color: $found-text;
        }
      }
    }
  }
</style>