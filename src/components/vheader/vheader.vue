<template>
<div class="header">
  <div class="content-wrapper">
    <div class="avatar">
      <img width="64" height="64" :src="seller.avatar">
    </div>
    <div class="content">
      <div class="title">
      <span class="brand"></span>
      <span class="name">{{seller.name}}</span>
      </div>
      <div class="description">
       {{seller.description}}{{seller.deliveryTime}}分钟送达
      </div>
      <div class="support" v-if="seller.supports">
      <span class="icon"></span>
      <span class="text">{{seller.supports[0].description}}</span>
    </div> 
    <div v-if="seller.supports" class="support-count" @click="Showdetail">
      <span class="count">{{seller.supports.length}}个</span>
    </div>   
    </div> 
    <div class="background">
      <img :src="seller.avatar" width="100%" height="100%">
    </div> 
  </div>
  <div class="bulletin-wrapper" @click="Showdetail(true)">
    <span class="bulletin-title"></span>
    <span class="bulletin-text">{{seller.bulletin}}</span>
  </div> 
  <div v-show="detailShow" class="detail">
    <div class="detail-wrapper">
      <div class="detail-main">
        <h1 class="name">{{seller.name}}</h1>
        <div class="star-wrapper">
          <star :size="48" :score="seller.score"></star>
        </div>  
      </div>
    </div> 
    <div class="detail-close" @click="Showdetail(false)">
      <span class="icon-close "></span>
    </div>  
  </div>
  
</div>
</template>

<script>

import star from "../star/star";

export default {
  props:["seller"],
  data(){
    return{
      detailShow:false,
    }
  },
  methods:{
    Showdetail(isShow){
      this.detailShow=isShow;
    }
  },
  components:{
    star
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .header{
     color:#fff;
     background-color: rgba(7,17,27,0.5);
     overflow: hidden;
  }
  .content-wrapper{
     padding: 24px 12px 18px 24px;
     font-size: 0;
     position: relative;
  }
  .avatar{
    display: inline-block;
    vertical-align: top;
  }
  .avatar img{
    border-radius: 2px;
  }
  .content{
    display: inline-block;
    font-size: 14px;
  }
  .title{
    margin: 2px 0 8px 0;
  }
  .brand{
    width: 30px;
    height: 18px;
    display: inline-block;
    background: url("brand@3x.png");
    background-size:30px 18px;
    background-repeat: repeat;
    vertical-align: top;
    margin-left:16px; 
  }
  .name{
    margin-left: 6px;
    font-size: 16px;
    line-height: 18px;
    font-weight: bold;
  }
  .description{
    margin-bottom: 10px;
    line-height: 12px;
    font-size: 12px;
    margin-left:16px; 
  }
  .support{
    margin-left: 16px;
  }
  .icon{
    display: inline-block;
    width: 12px;
    height:12px;
    margin-right: 4px;
    background: url('decrease_2@2x.png');
    background-size:12px 12px;
    background-repeat: repeat;
  }
  .text{
    line-height: 12px;
    font-size: 10px;
    vertical-align: top;
  }
  .support-count{
    position:absolute;
    right:12px ;
    bottom: 18px;
    padding: 0 8px;
    height: 24px;
    line-height: 24px;
    border-radius:14px;
    background-color: rgba(0,0,0,0.2);
    text-align:center;
  }
  .count{
    font-size: 10px
  }
  .bulletin-wrapper{
    position:relative;
    padding:0 12px;
    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
    height:28px;
    line-height:28px;
    background:rgba(7,17,27,0.2);
  }
  .bulletin-title{
    display:inline-block;
    width:22px;
    height:12px;
    vertical-align:middle;
    background: url('bulletin@2x.png'); 
    background-repeat:no-repeat;
    background-size:22px 12px;
  } 
  .bulletin-text{
    margin:0 4px;
    font-size:10px;
    font-weight:200;
  }
  .background{
    position:absolute;
    top:0;
    left:0;
    width: 100%;
    height: 100%;
    z-index:-1;
    filter: blur(10px);
  }
  .detail{
    position:fixed;
    top:0;
    left:0;
    right:0;
    bottom:0;
    background:rgba(7,17,27,0.8);
    z-index:100;
  }
  .detail-wrapper{
    min-height: 100%;
   
  }
  .detail-main{
    margin-top:64px;
    padding-bottom: 64px; 
  }
  .detail-close{
    text-align:center;
    line-height:32px;
    font-size :32px;
    height:32px;
    margin-top:-160px;
    color:rgba(255,255,255,0.5);
  }
  .name{
    text-align:center;
    font-size:16px;
    line-height :16px;
    font-weight :700;
    margin-bottom: 16px;
  }   
  .star-wrapper{
    margin-top:18px;
    padding: 2px 0;
    text-align: center;
    margin-left: -20px;
  }       
</style>
