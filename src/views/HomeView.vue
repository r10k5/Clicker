<script setup lang="ts">
import { ref } from 'vue'

const counter = ref(0);
const idMonitor = ref(0);
const currentMonitor = ref('src\\assets\\Monitor.svg');

const monitors = [
  'src\\assets\\Monitor.svg',
  'src\\assets\\Monitor2.svg'
];


function pcClick() {
  counter.value++;
}


function changeMonitor() {
  if (idMonitor.value === 0) {
    idMonitor.value = 1;
  } else {
    idMonitor.value = 0;
  }
  currentMonitor.value = monitors[idMonitor.value]
}
</script>

<template>
  <main>
    <div class ="main">
      <img class="backgraund" src="src\assets\Sprite-0002-Recovered.svg" />
      <img class="interact-object pc" src="src\assets\PC.svg" @click="pcClick" />
      <img class="interact-object monitor" :src="currentMonitor" @click="changeMonitor" />
      
      <div class="counter">
        {{ counter }}
      </div>
    </div>
  </main>
</template>

<style scoped>
.main{
  height: 900px;
  width: 1600px;
  display: flex;
  justify-content: center; /* главная ось */
  align-items: center; /* побочная ось */
  position: relative;
}
.backgraund {
  height: 900px;
  width: 1600px;
  z-index: 0;
}
.interact-object {
  z-index: 1;
  position: absolute;
}
.pc {
  height: 230px;
  width: 150px;
  top: 300px;
  left: 1060px;
}
.monitor{
  width: 420px;
  height: 210px;
  top:310px;
}
.counter{
  font-size: 40px;
  color:aliceblue;
  z-index: 1;
  position: absolute;
}
</style>
