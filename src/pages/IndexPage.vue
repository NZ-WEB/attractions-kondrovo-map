<template>
  <q-page class="flex flex-center">
    <div class="container">
      <div class="map">
        <q-img class="map__bg" src="~assets/kondr.png"/>
        <div class="map__pin chram">
          <q-btn @click="handleChange('charge')" :size="getSize('charge')" round :color="getColor('charge')" icon="star"></q-btn>
        </div>

        <div class="map__pin school">
          <q-btn  @click="handleChange('school')" :size="getSize('school')" round :color="getColor('school')" icon="star"></q-btn>
        </div>


      </div>

      <the-description :title="currentTitle" :text="currentTexts"/>

    </div>
  </q-page>
</template>

<script setup>

import TheDescription from "components/TheDescription";
import { ref } from "vue";
import {data} from "src/data/data";

const active = ref('school')

const currentTitle = ref(data.school.title);
const currentTexts = ref(data.school.texts);

const handleChange = (item) => {
  currentTitle.value = data[item].title;
  currentTexts.value = data[item].texts;

  active.value = item
}

const getColor = (item) => {
  if (active.value === item) {
    return 'red'
  }
  return 'primary'
}

const getSize = (item) => {
  if (active.value === item) {
    return 'md'
  }
  return 'sm'
}
</script>

<style lang="scss">
.container {
  max-width: 1400px;
  width: 100%;
  padding: 0 15px;
}

.map {
  position: relative;
  width: 100%;
  height: 600px;

  &__bg {
    width: 100%;
    height: 100%;
  }

  &__pin {
    position: absolute;
  }
}

.chram {
  top: 41%;
  left: 52%;
}

.school {
  top: 20%;
  left: 53.5%;
}


</style>
