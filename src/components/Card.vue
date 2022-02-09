<script setup>
  import {
    ref,
    reactive,
    computed
  } from 'vue'
  import html2canvas from 'html2canvas'
  import c1 from '../assets/c1.png'
  
  import attr1 from '../assets/1.png'
  import attr2 from '../assets/2.png'
  import attr3 from '../assets/3.png'
  import attr4 from '../assets/4.png'
  import attr5 from '../assets/5.png'
  import attr6 from '../assets/6.png'
  import attr7 from '../assets/7.png'
  import attr8 from '../assets/8.png'
  import attr9 from '../assets/9.png'

  import star from '../assets/star.png'

  const attrs = {
    attr1,
    attr2,
    attr3,
    attr4,
    attr5,
    attr6,
    attr7,
    attr8,
    attr9,
  }


  // defineProps({
  //   msg: String
  // })

  const count = ref(0)

  const info = reactive({
    type: "monster", //卡片類別
    color: "img/c1.png", //卡片顏色
    name: "遊戲王", //名字
    attr: 1, //屬性
    star: 1, //星數
    img: "", //圖像
    race: "", //族群
    text: "", //文字敘述
    atk: 0, //攻擊力
    def: 0 //防禦力
  })

  const preview_attr = computed(function(){
    return attrs[`attr${info.attr}`]
  })

  function preview($event){
    const img = $event.target.files[0];
    const url = window.URL.createObjectURL(img);
    info.img = url
    window.URL.revokeObjectURL(img);
  }

  function html2img() { //把HTML轉換成canvas
    html2canvas(document.querySelectorAll(".dc")[0], {
      useCORS: true
    }).then(canvas => {
      download(canvas);
    });
  }

  function download(x) { //下載圖片
    var anchor = document.createElement('a');
    document.body.appendChild(anchor);
    anchor.download = 'mycard.jpeg';
    anchor.href = x.toDataURL("image/jpeg", 1);
    anchor.click();
    anchor.remove();
  }

  // function data2html() { //把資料寫入obj--怪獸卡
  //   var img=document.getElementById("card_img").files[0];
  //   if (!img) {
  //     alert("未選擇圖片");
  //     return 0;
  //   } else if (img['type'] != 'image/gif' && img['type'] != 'image/jpeg' && img['type'] != 'image/png') {
  //     alert("上傳的檔案並非圖片");
  //     return 0;
  //   }
  //   var url = window.URL.createObjectURL(img);
  //   window.URL.revokeObjectURL(img);
  //   card_obj.type = document.getElementById("card_type").value;
  //   card_obj.color = document.getElementById("card_color").value;
  //   card_obj.name = document.getElementById("card_name").value;
  //   card_obj.attr = document.getElementById("card_attr").value;
  //   card_obj.star = document.getElementById("card_star").value;
  //   card_obj.img = url;
  //   card_obj.race = document.getElementById("card_race").value;
  //   card_obj.text = document.getElementById("card_text").value;
  //   card_obj.atk = document.getElementById("card_atk").value;
  //   card_obj.def = document.getElementById("card_def").value;
  //   card_output(card_obj);
  // }

  // function data2html_mort() { //把資料寫入obj--魔法卡/陷阱卡
  //   var img = document.getElementById("card_img_mort").files[0];
  //   if (!img) {
  //     alert("未選擇圖片");
  //     return 0;
  //   } else if (img['type'] != 'image/gif' && img['type'] != 'image/jpeg' && img['type'] != 'image/png') {
  //     alert("上傳的檔案並非圖片");
  //     return 0;
  //   }
  //   var url = window.URL.createObjectURL(img);
  //   window.URL.revokeObjectURL(img);
  //   card_obj.type = document.getElementById("card_type").value;
  //   card_obj.color = document.getElementById("card_color_mort").value;
  //   card_obj.name = document.getElementById("card_name_mort").value;
  //   card_obj.img = url;
  //   card_obj.text = document.getElementById("card_text_mort").value;
  //   card_output_mort(card_obj);
  // }

  // function list_c(x) { //改變輸入列表
  //   var input = document.querySelectorAll("#d1-r input");
  //   if (x == "monster") {
  //     document.getElementById("d1-m").style.display = "block";
  //     document.getElementById("d1-mort").style.display = "none";
  //   } else {
  //     document.getElementById("d1-m").style.display = "none";
  //     document.getElementById("d1-mort").style.display = "block";
  //   }
  //   for (let i = 0; i < input.length; i++) {
  //     input[i].value = "";
  //   }
  // }


</script>

<template>
  <div id="main">
    <div id="main-h">遊戲王卡生產器</div>
    <div id="red">預覽完成後點擊卡片即可下載。{{info.star}}</div>
    <div id="d1" >
      <div id="d1-l" @click="html2img">
        
        <div class="dc" @click="html2img">
          <img class="dc-color" :src="c1">
          <div class="dc-name">{{info.name}}</div>
          <img class="dc-attr" :src="preview_attr">
          <div class="dc-star">
            <img v-for="n in +info.star" :key="n" class="star" :src="star">
          </div>
          <img class="dc-img" :src="info.img">
          <div class="dc-race">【{{ info.race }}】</div>
          <div class="dc-text">{{ info.text }}</div>
          <div class="dc-add">ATK/{{ info.atk }}  DEF/{{info.def}} </div>
        </div>

      </div>
      <div id="d1-r">
        <!-- <div class='d1-r-d'>
          <span>卡片類別:</span>
          <select id="card_type" onchange=list_c(this.value)>
            <option value="monster">怪獸卡</option>
            <option value="magic">魔法卡</option>
            <option value="trap">陷阱卡</option>
          </select>
        </div> -->

        <div id="d1-m">
          <!-- <div class='d1-r-d'>
            <span>卡框:</span>
            <select id="card_color">
              <option value="img/c1.png">黃色</option>
              <option value="img/c2.png">紫色</option>
              <option value="img/c3.png">藍色</option>
              <option value="img/c4.png">白色</option>
              <option value="img/c5.png">灰色</option>
              <option value="img/c6.png">黑色</option>
              <option value="img/c7.png">綠色</option>
            </select>
          </div> -->
          <div class='d1-r-d'>
            <span>名字:</span>
            <input type="text" id="card_name" v-model="info.name">
          </div>
          <div class='d1-r-d'>
            <span>屬性:</span>
            <select id="card_attr" v-model="info.attr">
              <option value="1">闇</option>
              <option value="2">光</option>
              <option value="3">地</option>
              <option value="4">水</option>
              <option value="5">風</option>
              <option value="6">火</option>
              <option value="9">神</option>
            </select>
          </div>
          <div class='d1-r-d'>
            <span>星數:</span>
            <input type="range" step="1" min="0" max="13"  v-model="info.star">
            <!-- <select id="card_star" v-model="info.star">
              <option value="1">1</option>
              <option value="2">2</option>
              <option value="3">3</option>
              <option value="4">4</option>
              <option value="5">5</option>
              <option value="6">6</option>
              <option value="7">7</option>
              <option value="8">8</option>
              <option value="9">9</option>
              <option value="10">10</option>
              <option value="11">11</option>
              <option value="12">12</option>
              <option value="13">13</option>
            </select> -->
          </div>
          <div class='d1-r-d'>
            <span>圖像:</span>
            <input type="file" id="card_img" ref="img_preview" @change="preview">
          </div>
          <div class='d1-r-d'>
            <span>族群:</span>
            <input type="text" id="card_race" v-model="info.race">
          </div>
          <div class='d1-r-d'>
            <span>敘述:</span>
            <input type="text" id="card_text" v-model="info.text">
          </div>
          <div class='d1-r-d'>
            <span>攻擊力:</span>
            <input type="number" id="card_atk" v-model.number="info.atk">
          </div>
          <div class='d1-r-d'>
            <span>防禦力:</span>
            <input type="number" id="card_def" v-model.number="info.def">
          </div>
          <!-- <div id="dis_card" onclick=data2html()>預覽卡片</div> -->
        </div>

        <div id="d1-mort">
          <div class='d1-r-d'>
            <span>卡框:</span>
            <select id="card_color_mort">
              <option value="img/c1.png">黃色</option>
              <option value="img/c2.png">紫色</option>
              <option value="img/c3.png">藍色</option>
              <option value="img/c4.png">白色</option>
              <option value="img/c5.png">灰色</option>
              <option value="img/c6.png">黑色</option>
              <option value="img/c7.png">綠色</option>
            </select>
          </div>
          <div class='d1-r-d'>
            <span>名字:</span>
            <input type="text" id="card_name_mort">
          </div>
          <div class='d1-r-d'>
            <span>圖像:</span>
            <input type="file" id="card_img_mort">
          </div>
          <div class='d1-r-d'>
            <span>敘述:</span>
            <input type="text" id="card_text_mort">
          </div>
          <div id="dis_card" onclick=data2html_mort()>預覽卡片</div>
        </div>

      </div>

    </div>
  </div>
</template>

<style scoped>
</style>