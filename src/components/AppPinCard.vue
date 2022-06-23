<template>
  <q-card v-if="isOpened" class="custom-card">
    <q-item class="items-center justify-between">
      <h6 class="q-my-sm">{{ activeData.title }}</h6>
      <div class="column">
        <div>
          <q-btn @click="setIsOpened" size="sm" round icon="close"></q-btn>
        </div>
        <div class="q-my-sm">
          <q-btn
            :color="threeD ? 'secondary' : 'primary'"
            size="sm"
            @click="threeD = !threeD"
            round
          >
            3D
          </q-btn>
        </div>
      </div>
    </q-item>
    <q-img v-if="!threeD || !src3D" height="300px" :src="activeData.images[1]">
    </q-img>

    <div v-if="threeD" class="video">
      <iframe
        width="400"
        height="220"
        :src="src3D"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        autoplay="true"
      ></iframe>
    </div>
  </q-card>

  <q-dialog v-if="!src3D" v-model="threeD">
    <q-card>
      <q-card-section>
        <div class="text-h6">Секция 3D находится в стадии разработки</div>
      </q-card-section>

      <q-card-actions align="right">
        <q-btn flat label="OK" color="primary" v-close-popup />
      </q-card-actions>
    </q-card>
  </q-dialog>
</template>

<script setup>
import { data } from "src/data/data";
import { computed, ref } from "vue";

const props = defineProps({
  type: {
    type: String,
  },
  src3D: {
    type: String,
    default: null,
  },
});

const activeData = computed(() => {
  return data[props.type];
});

const isOpened = ref(true);
const threeD = ref(false);

const setIsOpened = () => (isOpened.value = !isOpened.value);
</script>

<style lang="scss" scoped>
.custom-card {
  z-index: 2;
  width: 400px;
  height: 300px;
}

.video {
  max-width: 400px;
}
</style>
