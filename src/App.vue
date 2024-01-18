<template>
  <div>
    <div class="black-bg" v-if="roomsIdx >= 0">
      <div class="white-bg">
        <h4>{{ rooms[roomsIdx].title }}</h4>
        <img :src="rooms[roomsIdx].image" class="room-img">
        <p>{{ rooms[roomsIdx].content }}</p>
        <button style="cursor: pointer" @click="roomsIdx = -1">닫기</button>
      </div>
    </div>

    <div class="menu">
      <a v-for="m in menu" :key="m">{{ m }}</a>
    </div>
    <img alt="Vue logo" src="./assets/logo.png">
    <div v-for="(r, idx) in rooms" :key="r" class="room">
      <img :src="r.image" class="room-img">
      <h4 style="cursor: pointer" @click="roomsIdx = idx">{{ r.title }}</h4>
      <p>{{ r.price }}원</p>
      <span style="cursor: pointer" @click="increaseLike(r)">좋아요: {{ r.like }}</span>
    </div>
  </div>
</template>

<script>
import data from './assets/data.js';
data;
export default {
  name: 'App',
  data(){
    return {
      roomsIdx: -1,
      menu: ['Home', 'Product', 'About'],
      rooms: data
    }
  },
  methods: {
    increaseLike: (room) => {
      room.like++;
    }
  },

  components: {
  }
}
</script>

<style>
body {
  margin: 0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

.menu {
  background-color: darkblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
  font: bold;
}
.room {
  background-color: blanchedalmond;
  border-radius: 10px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
