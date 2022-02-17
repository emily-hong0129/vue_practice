<template>
  <!-- 모달창 -->
  <div class="black-bg" v-if="modalIsOpen === true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지내용임</p>
      <button @click="nameClick">닫기</button>
    </div>
  </div>

  <div class="menu">
    <div>
      <a v-for="(a,i) in 메뉴들" :key="i">{{ a }}</a>
    </div>
  </div>

  <div class="itemDiv" v-for="(room, i) in 원룸들" :key="i">
    <img :src="room.image" :alt="room[i]" class="room-img">
    
    <h4 
      class="red" 
      :style="스타일" 
      @click="nameClick"
    >
      {{ room.title }}
    </h4>
    
    <p>{{ room.price }}원</p>
  </div>

</template>

<script>
// import { apple, apple2 } from './assets/data.js';  // import할 시 꼭 사용해야함
// console.log(apple);
// console.log(apple2);
import data from './assets/oneroom.js';

export default {
  name: 'App',
  data(){   // 데이터 보관함, 데이터는 객체 자료로 저장함
    return {
      스타일: 'color : blue',
      메뉴들 : ['Home', 'Shop', 'About'],
			room_name : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      price: [70, 60, 55],
      count: 0,
      countArr: [0, 0, 0],
      modalIsOpen: false, // 모달창
      원룸들:  data,
    }
  },
  components: {},
  methods: {
    increase: function(e){
      if(e.target.name === "button1") {
        this.countArr[0]++;

      }else if(e.target.name === "button2") {
        console.log(e.target.name);
        this.countArr[1]++;

      } else {
        console.log(e.target.name);
        this.countArr[2]++;

      }
    },
    nameClick : function(){
      if(this.modalIsOpen === false){
        this.modalIsOpen = true;
      }else{
        this.modalIsOpen = false;
      }
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.itemDiv {
  width: 50rem;
  height: auto;
  margin: 1em auto;
}

.room-img {
  width: 100%;
  height: 100%;
}

/* 모달창 */
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

</style>
