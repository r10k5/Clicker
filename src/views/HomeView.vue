<script setup lang="ts">
import { ref } from 'vue'

const counter = ref(0);

function pcClick() {
  counter.value++;
}
</script>

<template>
  <main>
    <div class ="main">
      <img class="backgraund" src="src\assets\Sprite-0002-Recovered.svg" />
      <img class="interact-object" src="src\assets\PC.svg" @click="pcClick"/>
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
  z-index: -1;
}
.interact-object {
  height: 230px;
  width: 150px;
  z-index: 4;
  position: relative;
  right: 540px;
  top: -40px;
}
.counter{
  font-size: 40px;
  color:aliceblue
}
</style>
