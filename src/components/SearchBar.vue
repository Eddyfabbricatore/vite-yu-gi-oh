<script>
  import {store} from '../data/store';

  export default {
    name:'SearchBar',
    data(){
      return{
        store
      }
    },

    methods:{
      reset(){
        store.nameToSearch = null;
        store.archetypeToSearch = null;

        this.$emit('startSearch');
      }
    }
  }
</script>

<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-auto">
        <select
          class="form-select me-5"
          aria-label="Default select example"
          v-model.trim="store.archetypeToSearch">
          <option
            :value="archetype"
            v-for="(archetype, index) in store.archetypesList"
            :key="index">{{ archetype }}</option>
        </select>
      </div>

      <div class="col-auto">
        <input
          type="text"
          class="form-control"
          placeholder="Fai la tua scelta"
          @keyup.enter="$emit('startSearch')"
          v-model.trim="store.nameToSearch">
      </div>

      <div class="col-auto">
        <button class="btn btn-info" @click="$emit('startSearch')">Cerca</button>
      </div>

      <div class="col-auto">
        <button class="btn btn-warning" @click="reset">Reset</button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @use '../scss/partials/variables' as *;

  .row{
    background-color: $bg-body !important;
  }
</style>