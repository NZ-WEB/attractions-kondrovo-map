<template>
  <div class="description">
    <h5 class="q-my-md">{{ title }}</h5>
    <p v-for="textItem of text" :key="textItem">{{ textItem }}</p>
    <q-btn label="Подробное описание" color="primary" @click="dialog = true" />

    <q-dialog full-width v-model="dialog">
      <q-card>
        <q-card-section>
          <h4 class="q-my-md">{{ title }}</h4>
          <p v-for="textItem of text" :key="textItem">{{ textItem }}</p>
          <div class="row q-gutter-sm">
            <div class="col-12 col-lg-5" v-for="url in images" :key="url">
              <q-img height="550px" fullwidth :src="url" />
            </div>
          </div>
        </q-card-section>
        <q-card-section class="row items-center q-gutter-sm">
          <q-btn v-close-popup label="Закрыть" color="primary" />
        </q-card-section>
      </q-card>
    </q-dialog>
  </div>
</template>

<script setup>
import { computed, ref } from "vue";
import { data } from "src/data/data";

const props = defineProps({
  title: {
    type: String,
  },
  text: {
    type: Array,
  },
  type: {
    type: String,
    default: null,
  },
});

const dialog = ref(false);
const images = computed(() => {
  return data[props.type].images;
});
</script>
