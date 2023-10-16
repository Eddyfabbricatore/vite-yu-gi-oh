<script>
  import axios from 'axios';
  import { store } from './data/store';
  import Header from './components/Header.vue';
  import SearchBar from './components/SearchBar.vue';
  import Main from './components/Main.vue';

  export default {
    name: 'App',
    components:{
      Header,
      SearchBar,
      Main
    },

    data(){
      return{
        store
      }
    },

    methods:{
      getApi(){
        axios.get(store.apiUrl, {
          params:{
            num: 20,
            offset: 0,
            name: store.nameToSearch,
            archetype: store.archetypeToSearch
          }
        })
        .then(res => {
          store.list = res.data.data;

          store.list.forEach( archetype => {
            if(!store.archetypesList.includes(archetype.archetype)){
              store.archetypesList.push(archetype.archetype);
            }
          })
        })
        .catch(err => {
          store.list = [];
        })
      }
    },

    mounted(){
      this.getApi();
    }
  }
</script>

<template>
  <Header title="Yu-Gi-Oh Api" />

  <SearchBar @startSearch="getApi" />

  <Main />
</template>

<style lang="scss">
  @use './scss/main.scss';
</style>