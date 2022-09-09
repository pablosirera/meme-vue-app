<script setup>
defineProps({
  meme: {
    type: Object,
    default: () => ({}),
  },
})
</script>

<template>
  <div class="card w-96 bg-base-100 shadow-xl">
    <figure class="px-10 pt-10">
      <img :src="meme.url" class="rounded-xl" />
    </figure>
    <div class="card-body items-center text-center">
      <h2 class="card-title">{{ meme.name }}</h2>
    </div>
  </div>
</template>
