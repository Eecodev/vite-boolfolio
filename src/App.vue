<template>
  <AppHeader/>
  <!-- la :key serve a non fare il reload della pagina, ma la rotta cambia senza fare il reload della pagina -->
  <router-view :key="$route.path"></router-view>
</template>

<script>
import {store} from './data/store';
import AppHeader from './components/AppHeader.vue';
  export default {
    name: "App",
    components: {
      AppHeader
    },
    data(){
      return{
        store,
      };
    },
    methods: {
      getApiTest(){
        axios.get(this.store.apiUrl + 'projects').then((res) =>{
          
        });
      }
    },
    mounted(){

    }
  }
</script>

<style lang="scss" scoped>
@use "./assets/styles/partials/variables" as *;


</style>