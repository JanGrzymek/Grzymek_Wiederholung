<template>
  <div>
    <div class="d-flex flex-wrap justify-space-around mx-12">
      <CarCard v-for="c of cars" :key="c.id" :car="c" @patchTitle="patchTitle($event)" />
    </div>
  </div>
</template>

<script>
import CarCard from './CarCard.vue';
import axios from 'axios';

export default {
  props: {
    cars: {
      Type: Array,
      default: () => [],
    },
  },
  components: { CarCard },
  methods: {
    async patchTitle(event) {
      console.log('step2');
      try {
        event.title += 'RESERVED';
        await axios({
          method: 'PATCH',
          url: 'http://localhost:3000/cars/' + event.id,
          'content-type': 'appplication/json',
          data: event,
        });
      } catch (error) {
        console.log(error);
      }
    },
    created() {
      this.getCards();
    },
  },
};
</script>
