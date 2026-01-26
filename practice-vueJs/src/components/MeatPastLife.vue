<script setup>
import { ref } from 'vue'

const meatType = ref('カルビ')
const meatPastLife = ref('')

const pastLifeList = [
  '飛ばないただの豚',
  'Wi-Fiルーター',
  'ミャク〇ャク様',
  'カルビ界の救世主'
]

function anotherPastLife() {
  const randomIndex = Math.floor(Math.random() * 4)
  meatPastLife.value = pastLifeList[randomIndex]
}
</script>

<template>
    <div id="app">
      <h1>肉の前世アプリ</h1>
      <p>この{{ meatType }}の前世は。。。</p>
      <h2>{{ meatPastLife }}</h2>
      <button @click="anotherPastLife">前世を見る</button>
    </div>
</template>

<style scoped></style>
