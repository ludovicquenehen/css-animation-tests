<script setup>
import { onMounted, ref } from 'vue'
import short from 'short-uuid'
const squares = ref([])
onMounted(() =>{
  const app = document.getElementById('app')
  setInterval(() => {
    const uid = short().generate();
    console.log(uid)
    const el = document.createElement('div')
    el.classList.add('square')
    el.id = uid
    squares.value.push(el)
    console.log('add')
    app.append(el)
    setTimeout(() => {
      const elToDelete = document.getElementById(uid)
      elToDelete.remove()
      const index = squares.value.findIndex(e => el.id === e.id)
      squares.value.splice(index, 1)
      console.log('pop')
    }, 12000)
  }, 1200)
})
</script>

<template>
<div class="square"></div>
</template>

<style>
.square {
  position: absolute;
  animation: 10s square linear;
  width: 500px;
  height: 500px;
  border-radius: 90px;
}

@keyframes square {
  0%
  {
    transform: scale(0) rotate(0deg);
    background-color: #FF0000;
    opacity: 1;
  }

  25%
  {
    transform: scale(0.25) rotate(45deg);
    background-color: #884400;
    opacity: 0.85;
  }

  50% {
    transform: scale(0.5) rotate(90deg);
    background-color: #EE8800;
    opacity: 0.75;
  }

  75%
  {
    transform: scale(0.75) rotate(135deg);
    background-color: #448800;
    opacity: 0.65;
  }

  100%
  {
    transform: scale(1) rotate(180deg);
    background-color: #00BB44;
    opacity: 0.5;
  }
}
</style>
