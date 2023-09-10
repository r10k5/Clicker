<script setup lang="ts">
import PersonalComputer from '@/components/icons/PersonalComputer.vue';
import MonitorState from '@/components/icons/MonitorState.vue';
import KeyboardMouseState from '@/components/icons/KeyboardMouseState.vue';
import VerticalMonitorState from '@/components/icons/VerticalMonitorState.vue';
import { ref } from 'vue'

const counter = ref(0);
const idMonitor = ref(0);
const pcType = ref<'dark' | 'light'>('dark');
const monitorType = ref<'off' | 'ystu'>('off');
const keyboardMouseType = ref<'dark' | 'light'>('dark');
const verticalMonitorType = ref<'off' | 'counter'>('off')

function pcClick() {
  counter.value++;
}

function changeMonitor() {
  if (idMonitor.value === 0) {
    idMonitor.value = 1;
    pcType.value = 'light';
    monitorType.value = 'ystu';
    keyboardMouseType.value = 'light'
  } else {
    idMonitor.value = 0;
    pcType.value = 'dark';
    monitorType.value = 'off';
    keyboardMouseType.value = 'dark'
  }
}
</script>

<template>
  <main>
    <div class ="main">
      <img class="backgraund" src="src\assets\Background.svg" />
      <PersonalComputer :type="pcType" @click="pcClick" /> 
      <!-- для svg используем компоненты vue -->
      <MonitorState :type="monitorType" @click="changeMonitor"/>
      <KeyboardMouseState :type="keyboardMouseType" />
      <VerticalMonitorState :type="verticalMonitorType" />
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

.counter{
  font-size: 40px;
  color:aliceblue;
  z-index: 1;
  position: absolute;
}
</style>
