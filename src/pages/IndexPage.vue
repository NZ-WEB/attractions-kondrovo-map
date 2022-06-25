<template>
  <q-page class="flex flex-start">
    <div class="container">
      <h5 class="q-my-sm">Достопримечательности города Кондрово</h5>
      <p>
        Основные достопримечательности города Кондрово показаны на интерактивной
        карте с описанием
      </p>

      <div class="map">
        <q-img height="500px" class="map__bg" src="~assets/kondr.png" />
        <app-pin
          type="charge"
          :active="active"
          :top="40"
          :left="52"
          @handleChange="handleChange"
          class="charge"
          src3D="https://www.youtube.com/embed/SXOJnTnjFYs?controls=0?autoplay=1"
        />
        <app-pin
          type="school"
          :active="active"
          :top="8"
          :left="53.5"
          @handleChange="handleChange"
          class="school"
          src3D="https://www.youtube.com/embed/bYsiHFfskdU?controls=0"
        />
        <app-pin
          type="factory"
          :active="active"
          :top="84"
          :left="57"
          @handleChange="handleChange"
          class="factory"
          src3D="https://www.youtube.com/embed/o8bqtoDv9dg?controls=0&amp;start=10"
        />
        <app-pin
          type="ploshad"
          :active="active"
          :top="37"
          :left="62"
          @handleChange="handleChange"
          class="ploshad"
          src3D="https://www.youtube.com/embed/aNX5ylMlajk?controls=0"
        />
        <app-pin
          type="shop"
          :active="active"
          :top="30"
          :left="54"
          @handleChange="handleChange"
          class="shop"
          src3D="https://www.youtube.com/embed/UTHjRqYSf7Q/controls=0"
        />
        <app-pin
          type="kondirev"
          :active="active"
          :top="32"
          :left="52"
          @handleChange="handleChange"
          class="shop"
          src3D="https://www.youtube.com/embed/lcIjdVnP4oI?controls=0"
        />
      </div>

      <the-description
        :title="currentTitle"
        :text="currentTexts"
        :type="active"
      />

      <p style="position: absolute; color: #fff">Автор nz-web - kann1ball</p>
    </div>
  </q-page>
</template>

<script setup>
import TheDescription from "components/TheDescription";
import { ref } from "vue";
import { data } from "src/data/data";
import AppPin from "components/AppPin";

const active = ref("school");

const currentTitle = ref(data.school.title);
const currentTexts = ref(data.school.texts);

const handleChange = (item) => {
  currentTitle.value = data[item].title;
  currentTexts.value = data[item].texts;

  active.value = item;
};
</script>

<style lang="scss">
.container {
  max-width: 1600px;
  width: 100%;
  padding: 0 15px;
  margin: 0 auto;
}

.map {
  position: relative;
  width: 100%;

  &__bg {
    width: 100%;
    height: 100%;
  }

  &__pin {
    position: absolute;
  }
}

@media (max-width: 1300px) {
  .school {
    top: 14% !important;
  }

  .shop {
    top: 32% !important;
  }

  .kondirev {
    top: 34% !important;
  }
}
@media (max-width: 1000px) {
  .school {
    top: 19% !important;
  }

  .shop {
    top: 34% !important;
  }

  .kondirev {
    top: 35% !important;
  }
  .charge {
    top: 42% !important;
  }
  .ploshad {
    top: 40% !important;
  }
}
@media (max-width: 760px) {
  .ploshad {
    left: 67% !important;
  }
}
@media (max-width: 450px) {
  .ploshad {
    left: 78% !important;
  }
  .school {
    left: 55% !important;
  }

  .shop {
    left: 57% !important;
  }
}
</style>
