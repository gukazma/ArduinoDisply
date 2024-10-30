<template>
  <div class="container d-flex flex-column justify-content-center align-items-center" style="height: 100vh; background-color: #f2f2f2;">
    <div class="content text-center p-4" style="background-color: #fff; border-radius: 5px; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);">
      <button @click="openPort">输出端口信息</button>
      <input v-model="com" placeholder="串口">
      <input v-model="frequency" placeholder="频率">
      <p>端口输出：{{ message }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref,onMounted} from 'vue'
const com = ref('')
const frequency = ref('')
const message = ref('')
window.electron.electronAPI.ipcRenderer.on("reply",(event,data)=>{
    console.log(data);
})
function openPort() {
  // ...
  const func = async () => {
     var data = { 
      com: '',
      freg: ''
     }
     data.com = "COM0";
     data.freg = 9600;
    const response = await window.serialport.onport(data);
    console.log(response);// prints out 'pong'
    message.value = response;
  }
  func()
  window.electron.ping()
}
</script>
