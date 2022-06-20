<template>
    <div v-if="isModalOpen == true" class="black-bg">
    <div class="white-bg">
        <h4>{{ oneroom[modalContents].title }}</h4>
        <img :src="oneroom[modalContents].image" class="room-img">
        <p>{{ oneroom[modalContents].content }}</p>
        <p>{{ oneroom[modalContents].price }}</p> <br>
        <Discount/>
        <!-- <button @click="isModalOpen = false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
    name: 'Modal',
    props : {
        oneroom : Object, // 자식은 props로 받은 데이터를 등록 -> props : {데이터 key : 데이터의 자료형}
        isModalOpen : Boolean,
        modalContents : Number,
    }
}
</script>

<style>

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