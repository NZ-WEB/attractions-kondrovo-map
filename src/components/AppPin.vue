<template>
  <div class="map__pin" :style="getPosition">
    <q-btn
      @click="$emit('handleChange', type)"
      :size="getSize(type)"
      round
      :color="getColor(type)"
      icon="star"
    ></q-btn>
    <AppPinCard :type="type" v-if="active === type" />
  </div>
</template>

<script setup>
import { data } from "src/data/data";
import { computed, ref, toRef, watch } from "vue";
import AppPinCard from "./AppPinCard.vue";

const props = defineProps({
  type: {
    type: String,
  },
  top: {
    type: Number,
  },
  left: {
    type: Number,
  },
  active: {
    type: String,
  },
});

const activeRef = toRef(props.active);

const emits = defineEmits({
  handleChange: null,
});

const getPosition = computed(() => {
  return `top: ${props.top}%; left: ${props.left}%`;
});

const getColor = (item) => {
  if (props.active === item) {
    return "red";
  }
  return "primary";
};

const getSize = (item) => {
  if (props.active === item) {
    return "md";
  }
  return "sm";
};
</script>
