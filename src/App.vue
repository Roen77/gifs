<template>
  <div class="app">
    <h2>Gif Search</h2>
    <search @fetch-gifs="onFetch"></search>
    <gif-list :gifs="gifs"></gif-list>
  </div>
</template>

<script>
import GifList from './components/GifList.vue'
import Search from './components/Search.vue'


export default {
  name: 'App',
  components: {
    Search,
    GifList
   
  },
  data(){
    return{
      gifs:[]
    }
  },
  methods: {
    onFetch(result) {
      this.gifs=result;
    }
  },
}
</script>

<style>
*{margin: 0; padding: 0;}
body{
  box-sizing: border-box;
  padding: 50px;
}
.app h2{text-align: center; font-size: 3rem;}
</style>
