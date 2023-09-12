<script setup lang="ts">
import PersonalComputer from '@/components/icons/PersonalComputer.vue';
import MonitorState from '@/components/icons/MonitorState.vue';
import KeyboardMouseState from '@/components/icons/KeyboardMouseState.vue';
import VerticalMonitorState from '@/components/icons/VerticalMonitorState.vue';
import { ref } from 'vue'

const counter = ref(0);
const idMonitor = ref(0);
const idVerticalMonitor = ref(0);
const pcType = ref<'dark' | 'light'>('dark');
const monitorType = ref<'off' | 'ystu' | 'win'>('off');
const keyboardMouseType = ref<'dark' | 'light'>('dark');
const verticalMonitorType = ref<'off' | 'counter' | 'windows'>('off')

function keyboardClick() {
  if (monitorType.value === 'ystu') {
    counter.value++;
  }
}

function changeMonitor() {
  idMonitor.value = (idMonitor.value + 1) % 3;
  switch (idMonitor.value) {
    case 0: {
      monitorType.value = 'ystu';
      break;
    }
    case 1: {
      pcType.value = 'dark';
      monitorType.value = 'off';
      keyboardMouseType.value = 'dark'
      break;
    }
    case 2: {
      pcType.value = 'light';
      monitorType.value = 'win';
      keyboardMouseType.value = 'light';
      break;
    }
  }
}

function changeVerticalMonitor() {
  idVerticalMonitor.value = (idVerticalMonitor.value + 1) % 3;
  switch (idVerticalMonitor.value) {
    case 0: {
      verticalMonitorType.value = 'off';
      break;
    }
    case 1: {
      verticalMonitorType.value = 'windows';
      break;
    }
    case 2: {
      verticalMonitorType.value = 'counter';

      break;
    }
  }
}
</script>

<template>
  <main>
    <div class ="main">
      <img class="backgraund" src="src\assets\Background.svg" />
      <PersonalComputer :type="pcType" /> 
      <!-- для svg используем компоненты vue -->
      <MonitorState :type="monitorType" @click="changeMonitor"/>
      <KeyboardMouseState :type="keyboardMouseType" @click="keyboardClick" />
      <VerticalMonitorState :type="verticalMonitorType" @click="changeVerticalMonitor" />
      <div v-show="verticalMonitorType === 'counter'" class="counter">
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
  color:rgb(13, 35, 54);
  z-index: 1;
  position: absolute;
  left: 540px;
  top: 330px;
}
</style>
