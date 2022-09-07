<script setup>
import { ref } from '@vue/reactivity'
import HelloWorld from './components/HelloWorld.vue'
import HeartIcon from './components/HeartIcon.vue'

const memes = ref([])
const loadData = async () => {
  const response = await fetch('https://api.imgflip.com/get_memes')
  const { data } = await response.json()

  console.log(data.memes)
  memes.value = data.memes
}

loadData()
</script>

<template>
  <h1>Meme Search</h1>
  <section class="container">
    <div v-for="meme in memes" :key="meme.id" class="card">
      <HeartIcon class="icon" />
      <img :src="meme.url" />
      {{ meme.name }}
    </div>
  </section>
</template>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
}
.card {
  display: flex;
  flex-direction: column;
  border: 1px solid lightblue;
  border-radius: 8px;
  margin: 5px;
  position: relative;
  max-width: 180px;
  padding: 10px;
  align-items: center;
}
.card .icon {
  width: 30px;
  color: black;
  position: absolute;
  right: 15px;
  cursor: pointer;
}
.card .icon:hover {
  opacity: 0.75;
}
.card .icon.fav {
  color: red;
}
.card img {
  width: 180px;
}
</style>
