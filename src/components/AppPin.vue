<template>
  <div class="map__pin" :style="getPosition">
    <q-btn @click="this.$emit('handleChange' ,type)" :size="getSize(type)" round :color="getColor(type)" icon="star"></q-btn>
  </div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  type: {
    type: String
  },
  top: {
    type: Number
  },
  left: {
    type: Number
  },
  active: {
    type: String
  }
})

const emits = defineEmits({
  'handleChange': null,
})

const getPosition = computed(() => {
  return `top: ${props.top}%; left: ${props.left}%`
})

const getColor = (item) => {
  if (props.active === item) {
    return 'red'
  }
  return 'primary'
}

const getSize = (item) => {
  if (props.active === item) {
    return 'md'
  }
  return 'sm'
}

</script>
