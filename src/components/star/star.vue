<template>
  
   <div class="star" :class="starType">
     <span v-for="itemClass in itemClasses" :class="itemClass" class="star-item"></span>
   </div>    

</template>

<script>
const LENGTH=5;
const CLS_ON="on";
const CLS_HALF="half";
const CLS_OFF="off";


export default {
  props:{
      size:Number,
      score:Number,
  },
  computed:{
      starType(){
          return "star-"+this.size
      },
      itemClasses(){
          let result=[];
          let score=Math.floor(this.score*2)/2;
          let hasDecimal=score%1!==1;
          let integer=Math.floor(score);
          for(let i=0;i<integer;i++){
              result.push(CLS_ON)
          };
          if(hasDecimal){
              result.push(CLS_HALF)
          };
          while(result.length<LENGTH){
              result.push(CLS_OFF)
          };
          return result;    
     }   
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import "../../common/stylus/mixins.styl"

.star-item
      display inline-block
      width 10px
      height 10px
      background-repeat no-repeat
      background-size 10px 10px
      margin-left 3px
    .on
      bg-star(star24_on)
    .half
      bg-star(star24_half)
    .off
      bg-star(star24_off)
  .star-36
    .star-item
      display inline-block
      width 15px
      height 15px
      background-repeat no-repeat
      background-size 15px 15px
      margin-left 6px
      
    .on
      bg-star(star36_on)
    .half
      bg-star(star36_half)
    .off
      bg-star(star36_off)
  .star-48
    .star-item
      display inline-block
      width 20px
      height 20px
      background-repeat no-repeat
      background-size 20px 20px
      margin-left 22px
    .on
      bg-star(star48_on)
    .half
      bg-star(star48_half)
    .off
      bg-star(star48_off)

</style>
