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
import { ref,onMounted } from 'vue'
const com = ref('')
const frequency = ref('')
const message = ref('')
function openPort() {
  // ...
  message.value = "12312"
  const func = async () => {
    const response = await window.electron.ping()
    console.log(response) // prints out 'pong'
  }
  func()
  window.electron.ping()
}
</script>
