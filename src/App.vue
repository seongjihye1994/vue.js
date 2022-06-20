<template>

  <Modal :oneroom="oneroom" :isModalOpen="isModalOpen" :modalContents="modalContents"/> <!-- 부모가 가진 아래의 데이터를 골라서 <자식 :데이터="데이터"> 형식으로 자식에게 전송 -->

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a> <!-- Vue.js 의 반복문 문법 v-for="변수 in 반복 횟수" :key="변수"-->
  </div>

  <Discount/> <!-- Discount Key로 import 해 온 Discount를 사용 --> 

  <Card @modalOpen="isModalOpen = true; modalContents = $event" :oneroom="oneroom[i]" v-for="(작명, i) in oneroom" :key="작명" />
  <!-- 자식이 보낸 @modalOpen 메세지를 받음
       @click="$emit('modalOpen', oneroom.title)으로 자식이 함수와 데이터를 전송하면
       그 함수와 데이터를 부모가 받아 사용 가능(전송한 데이터(oneroom.id)는 $event 로 받음)
   -->
</template>

<script>

import oneroom from './assets/oneroom.js';
import Discount from './Discount.vue'; // Discount Key로 import
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data() { // 데이터 바인딩을 위한 데이터 보관함
    return {
      // 오브젝트 : { name : 'kim', age : 20},
      oneroom : oneroom,
      modalContents : 0,
      isModalOpen : false,
      메뉴들 : ['Home', 'Shop', 'About'],
    }
  },
  methods : {
    increase(i) {
      this.report[i]++;
    }
  },
  components: {
    Discount : Discount, // Discount Key로 import 해 온 Discount를 등록
    Modal : Modal,
    Card : Card,
  }
}
</script>

<style>
body {
  margin: 0;
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
</style>
