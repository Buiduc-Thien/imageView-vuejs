<template>
<div id="slide">
<div> 
<ul>
  <button
  @click="next"
  >Next</button>
  <li
  v-for="(image, index) in images"
  :key="index"
  v-show="index == imgShowing"
  ><img :src="image.source" alt="">
  </li>
  <button
  @click="back"
  >Back</button>
</ul>

<ul id="picked">
  
  <li 
  v-for="(image, index) in images"
  @click="imgShowing= index"
  :key="index">
  {{index}}
  <span></span>
  </li>
  
</ul>
</div>
</div>
  
</template>

<script>
export default {
    data(){
      return{
        imgShowing: 0,
        show: false,
        images:[
          { source: 'https://i.pinimg.com/originals/e1/61/d5/e161d573eb8616af64bbba0108f58d06.png'},
          { source:'https://2.bp.blogspot.com/-hQO4N8fZDu0/XD4zZDt34gI/AAAAAAAAAno/XubT6cXTxboyNKLCls1mhuMZ6IhzWZu4gCKgBGAs/w0/forest-landscape-art-8-4k.jpg'},
          { source:'https://www.teahub.io/photos/full/70-703376_dark-forest-wallpaper-art.jpg'},
          { source:'https://wallpaperaccess.com/full/6264342.jpg'}
        ]
      }
    },
    methods: {
      next(){
        this.imgShowing++;
        if (this.imgShowing == this.images.length){
          this.imgShowing = 0;
        }
      },
      back(){
        this.imgShowing--;
        if (this.imgShowing == -1){
          this.imgShowing = this.images.length -1;
        }
      }
    }
}
</script>

<style scoped>
#slide{
  display: flex;
  justify-content: center;
}
img{
  max-width: 500px;
}
ul li{
  display: inline;
  cursor: pointer;
  } 
ul#picked li{
  color: aliceblue;
  text-align: center;
  line-height: 50px;
  display: inline-block;
  cursor: pointer;
  background: #456BD9;
  clip-path: circle(50%);
  height: 50px;
  width: 50px;
  } 

</style>