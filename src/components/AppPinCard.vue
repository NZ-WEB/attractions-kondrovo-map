<template>
  <q-card v-if="isOpened" class="custom-card">
    <q-item class="items-center">
      <h6 class="q-my-sm">{{ activeData.title }}</h6>
      <q-card-section>
        <q-btn @click="setIsOpened" size="sm" round icon="close"></q-btn>
      </q-card-section>
    </q-item>
    <q-img :src="activeData.images[0]"> </q-img>
  </q-card>
</template>

<script setup>
import { data } from "src/data/data";
import { computed, ref } from "vue";

const props = defineProps({
  type: {
    type: String,
  },
});

const activeData = computed(() => {
  return data[props.type];
});

const isOpened = ref(true);

const setIsOpened = () => (isOpened.value = !isOpened.value);
</script>

<style lang="scss" scoped>
.custom-card {
  z-index: 2;
  width: 400px;
  height: 300px;
}
</style>
