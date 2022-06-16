<template>
  <div class="description">
    <h5 class="q-my-md">{{ title }}</h5>

    <p v-for="textItem of text" :key="textItem">{{textItem}}</p>
  </div>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String
  },
  text: {
    type: Array,
  }
})

</script>
