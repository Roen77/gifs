<template>
    <div id="giflist">
         <gif v-for="gif in gifs" :key="gif.id" :gif="gif"></gif>
    </div>
</template>

<script>
import Gif from './Gif.vue'
export default {
    components:{Gif},
    props:{
        gifs:{
            type:Array,
            required:true
        }
    }

}
</script>

<style>
#giflist{
    display: flex;
    flex-wrap:wrap;
    /* justify-content: space-between; */
}
</style>