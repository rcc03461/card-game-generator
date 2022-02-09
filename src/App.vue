<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Card from './components/Card.vue'
</script>

<template>
  <Card msg="Hello Vue 3 + Vite" />
</template>

<style>
#main {
  width:800px;
  background-color:#fff;
  margin:0 auto;
  border-radius:10px;
  box-shadow:0 0 10px #222;
  overflow:hidden;
  font-family:微軟正黑體;
  position:relative;
}
.dc {
  width:400px;
  height:580px;
  font-family:標楷體;
  position:relative;
  user-select: none; 
  cursor: pointer;
}
.dc-color {
  width:400px;
  height:580px;
}
.dc-name {
  font-weight:bold;
  font-size:30px;
  position:absolute;
  top:35px;
  left:45px;
}
.w {
  color:#fff;
}
.dc-attr {
  width:35px;
  height:35px;
  position:absolute;
  top:37px;
  right:45px;
}
.dc-star {
  width:312px;
  position:absolute;
  top:85px;
  right:45px;
}
.star {
  width:22px;
  height:22px;
  margin:0 0 0 2px;
  float:right;
}
.bs {
  float:left;
}
.dc-img {
  width:286px;
  height:286px;
  position:absolute;
  top:126px;
  left:58px;
}
.b {
  width:285px;
  height:289px;
  position:absolute;
  top:125px;
  left:58px; 
}
.dc-race {
  font-size:20px;
  position:absolute;
  top:445px;
  left:35px;  
  font-weight: bold;
}
.recemort {
  position:absolute;
  top:85px;
  right:45px;
  font-size:21px;
}
.dc-text {
  width:320px;
  height:55px;
  word-wrap:break-word;
  overflow:hidden;
  font-size:16px;
  position:absolute;
  top:469px;
  left:40px;  
  border-style: solid;
  border-width: 0 0 1px 0;
  font-weight: bold;
}
.m {
  top:445px;
  left:40px; 
  border-width: 0;
}
.dc-add {
  position:absolute;
  top:525px;
  right:40px;  
}
#main-h {
  height:50px;
  line-height:50px;
  background-color:#CA7A2C;
  color:#fff;
  font-size:25px;
  font-weight:bold;
  text-align:center;
}
#d1 {
  padding:10px 20px;
  overflow:hidden;
}
#d1-l {
  width:400px;
  float:left;
  box-shadow:0 0 10px #222;
}
#d1-r {
  padding:0 0 0 50px;
  float:left;
}
.d1-r-d {
  padding:10px 0 10px 0;
  font-size:25px;
  border-style: solid;
  border-width: 0 0 1px 0;
}
.d1-r-d input,.d1-r-d select {
  width:200px;
  font-size:25px;
  float:right;
  font-family:微軟正黑體;
}
#dis_card {
  margin:10px 0 0 0;
  height:50px;
  line-height:50px;
  background-color:#CA7A2C;
  color:#fff;
  font-size:25px;
  font-weight:bold;
  text-align:center; 
  cursor: pointer;
  user-select: none;
}
#dis_card:hover {
  box-shadow:0 0 5px #222;
}
#card_img,#card_img_mort {
  font-size:16px;
}
#red {
  color:#f00;
  font-size:16px;
  text-align:center;
}
#d1-mort {
  display:none;
}
</style>
