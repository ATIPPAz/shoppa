<template>
  <v-card>
    <v-card-title> {{ ProductData.name }} </v-card-title>
    <v-img :src="ProductData.url" aspect-ratio="1.5" contain></v-img>
    <v-card-text> ราคา : {{ ProductData.Price }} </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    ProductData: {
      type: Object,
      default: () => {},
    },
  },

  data() {},
};
</script>

<style></style>
