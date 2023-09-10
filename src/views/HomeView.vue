<script setup lang="ts">
import PersonalComputer from '@/components/icons/PersonalComputer.vue';
import MonitorState from '@/components/icons/MonitorState.vue';
import { ref } from 'vue'

const counter = ref(0);
const idMonitor = ref(0);
const pcType = ref<'dark' | 'light'>('dark');
const monitorType = ref<'off' | 'ystu'>('off');
// чо?
const currentMonitor = ref('src\\assets\\Monitor-off.svg');

const monitors = [
  'src\\assets\\Monitor-off.svg',
  'src\\assets\\Monitor-ystu.svg'
];

function pcClick() {
  counter.value++;
}


function changeMonitor() {
  if (idMonitor.value === 0) {
    idMonitor.value = 1;
    pcType.value = 'light';
    monitorType.value = 'ystu';
  } else {
    idMonitor.value = 0;
    pcType.value = 'dark';
    monitorType.value = 'off';
  }
  currentMonitor.value = monitors[idMonitor.value]
}
</script>

<template>
  <main>
    <div class ="main">
      <img class="backgraund" src="src\assets\Background.svg" />
      <PersonalComputer :type="pcType" @click="pcClick" /> 
      <!-- для svg используем компоненты vue -->
      <MonitorState :type="monitorType" @click="changeMonitor"/>
      <img class="interact-object keyboard-mouse" src="src\assets\KeyboardMouse.svg"/>
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
.monitor{
  width: 320px;
  height: 220px;
  top: 340px;
  left: 660px;
}
.keyboard-mouse{
  width: 330px;
  height: 20px;
  top: 560px;
  left: 670px;

}
.counter{
  font-size: 40px;
  color:aliceblue;
  z-index: 1;
  position: absolute;
}
</style>
