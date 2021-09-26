<template>
  <div>
    <v-card class="mx-auto my-12" max-width="374">
      <v-img height="250" :src="car.image"></v-img>

      <v-card-title>{{ car.title }}</v-card-title>

      <v-card-text>
        <div>
          Owner: {{ car.owner.firstName }} {{ car.owner.lastName }}<br /><br />
          Year: {{ car.yearOfMake }} <br />
          Miles: {{ car.miles }}<br /><br />
          Price: {{ car.price }}<br /><br />
          {{ car.description }}
        </div>
      </v-card-text>

      <v-divider class="mx-4"></v-divider>

      <v-card-actions>
        <v-btn color="error" @click="buttonClick()"> Buy Now </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    car: {
      type: Object,
      default: () => {},
    },
  },
  methods: {
    buttonClick() {
      this.$emit('patchTitle', this.car);
    },
  },
};
</script>
