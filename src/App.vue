<script setup>
import { ref } from 'vue'
const h1 = 'Vue Practice'
const h2 = 'Random Password'

const numbers = '0987654321'
const symbols = '!@#$%^&*+=-'
const upperCase = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
const lowerCase = 'abcdefghijklmnopqrstuvwxyz'
const allChars = numbers + symbols + upperCase + lowerCase

const inpNum = ref(6)
const randomPassword = ref('')
let result = ''

const generate = () => {
  let i = 0
  for (i = 0; i < inpNum.value; i++) {
    const randomindex = Math.floor(Math.random() * allChars.length)
    result += allChars[randomindex]
  }
  randomPassword.value = result
}

const copy = async () => {
  if (result === '') {
    alert('密碼正在從宇宙飛來的路上 🚀 請稍候')
    return
  }
  await navigator.clipboard.writeText(randomPassword.value)
  alert('已複製密碼！')
}
</script>

<template>
  <div class="container">
    <h1>{{ h1 }}</h1>
    <h2>{{ h2 }}</h2>
    <input class="inpNum" type="number" min="6" max="15" v-model="inpNum" />
    <input class="showPassword" type="text" v-model="randomPassword" />
    <button id="copy" @click="copy">Copy</button>
    <button id="generate" @click="generate">Generate</button>
  </div>
</template>

<style scoped>
@import './0506.css';
</style>
