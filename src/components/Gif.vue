<template>
        <div class="gifwrap">
            <div class="gif" :style="`background-image:url(${gif.images.original.url})`">
               <div class="copyinput">
                    <input ref="url" type="text" :value="gif.images.original.url">
                <button class="copybutton" @click="copyUrl">copy</button>
               </div>
            </div>
        </div>
</template>

<script>
export default {
    data() {
        return {
             copyed:false
        }
    },
    props:{
        gif:{
            type:Object,
            required:true,
        }
    },
    methods: {
        copyUrl() {
            if(this.copyed){
               this.copyed=false 
                this.$refs.url.value=this.gif.images.original.url
                return
            }
            this.copyed=true;
            this.$refs.url.select();
            document.execCommand('copy');
            this.$refs.url.value="Copied!"


        },
    },
 

}
</script>

<style>
.gifwrap{
    position: relative;
    margin: 1%;
    width:31.333%;
    box-sizing: border-box;
    padding: 10px;
    height: 400px;
    /* height: 31.333%; */
   
    /* flex:0 27% 1; */
}
.gifwrap p{
    position: absolute; border: 1px solid #ddd;
    right: 0;
    top:-55%;
}
.gifwrap .gif{position: absolute; left:50%; top:50%; transform: translate(-50%,-50%); width: 100%; height: 100%;   background-repeat: no-repeat;
background-position: center;
    background-size: contain; box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);}
    .gifwrap .gif .copyinput{position: absolute; left:0; bottom:0; display: flex; width: 100%;}
    .gifwrap .gif .copyinput button{cursor: pointer; width: 50px; background-color: royalblue; color:#fff;  box-sizing: border-box;
  border:none;
  box-shadow: 0 0 5px rgb(30, 143, 255);}
@media screen and (max-width:1073px) {
    .gifwrap{width: 48%;}
}
@media screen and (max-width:600px) {
    .gifwrap{width: 100%;}
}
</style>