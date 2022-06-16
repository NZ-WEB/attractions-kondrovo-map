<template>
  <q-page class="flex flex-center">
    <div class="container">
      <div class="map">
        <q-img class="map__bg" src="~assets/kondr.png"/>
        <div class="map__pin chram">
          <q-btn size="sm" round color="primary" icon="star"></q-btn>
        </div>
      </div>

      <div class="description">
        <h5 class="q-my-md">Кондровская  средняя общеобразовательная  школа №1</h5>
        <p>Кондровская  средняя общеобразовательная  школа №1 была открыта в 1937 году. Из переполненной  школы  второй ступени  перевели в "новостройку" часть учеников</p>

        <p>В годы Великой Отечественной войны с 1941 г. по 1943 г. в здании школы располагался госпиталь, учеба началась в стенах "новостройки"  лишь с осени 1943 года. Первый выпуск учащихся пришелся на второе послевоенное лето.</p>

        <p>На территории школы открыты два памятника: один напротив входа в честь Учителей, которые ушли на фронт и не вернулись. 23 апреля 2015 г. на этом памятнике была открыта Мемориальная доска участникам и ветеранам  Великой Отечественной войны, работавшим в школе.</p>
      </div>
    </div>
  </q-page>
</template>

<script setup>

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


</style>
