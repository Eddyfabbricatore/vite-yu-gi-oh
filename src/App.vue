<script>
import axios from 'axios';
import { store } from './data/store';
import Header from './components/Header.vue';

export default {
  name: 'App',
  components:{
    Header
  },
  data(){
    return{
      store
    }
  },
  methods:{
    getApi(){
      axios.get(store.apiUrl)
      .then(res => {
        store.list = res.data;
        console.log(store.list);
      })
      .catch(err => {
        console.log(err);
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
</template>

<style lang="scss">
  @use './scss/main.scss';
</style>