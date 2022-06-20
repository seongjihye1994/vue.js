<template>
    <div>
      <img :src="oneroom.image" class="room-img">
      <h4 @click="modalOpen">{{ oneroom.title }}</h4> 
      <!-- 자식이 부모의 데이터를 수정하고 싶다면 $emit(함수명, 데이터) 으로 
      부모에게 메세지를 전달 -->
      <p>{{ oneroom.price }}원</p>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props : {
        oneroom : Object,
    },
    method : {
      modalOpen() {
        this.$emit('modalOpen', this.oneroom.id);
      }
    }
}
</script>

<style>
div {
  box-sizing: border-box;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>