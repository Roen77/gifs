<template>
  <div>
      <input @click="resetinput" type="text" placeholder="search for awesome gifs" v-model="keyword" @input="onInput">
  </div>
</template>

<script>
export default {
//3veitOn3rVMzPMduGVEOxl31SHXXSfc1
data() {
  return {
    keyword: '',
    timeout:null,
  }
},
 methods:{
     onInput(){
       clearTimeout(this.timeout)
      this.timeout=setTimeout(()=>{
          this.search();
        },500)
     },
     search(){
        fetch(`https://api.giphy.com/v1/gifs/search?api_key=3veitOn3rVMzPMduGVEOxl31SHXXSfc1&q=${this.keyword}&limit=9`)
         .then((response)=>response.json())
         .then(result=>{
          //  this.gifs=result.data;
           this.$emit('fetch-gifs',result.data)
         })
     },
     resetinput(){
       this.keyword=''
     }
 }
}
</script>

<style>
input{
  display: block;
  padding: 10px 16px;
  border-radius: 4px;
  font-size: 18px;
  outline:0;
  border:2px solid #5f5f5f;
  width: 100%;
  box-sizing: border-box;
  border:none;
  box-shadow: 0 0 5px rgb(30, 143, 255);
}
input:focus{
  border-color:rgb(15, 105, 196);
  box-shadow: 0 0 10px royalblue;
}
input:focus::placeholder{
  opacity: 0;
}
</style>