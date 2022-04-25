<template>
  <v-card>
    rasdas
    <!-- <v-card-title> {{ Product.name }} </v-card-title> -->
    <!-- <v-img :src="Product.url" aspect-ratio="1.5" contain></v-img> -->
    <!-- <v-card-text> ราคา : {{ Product.Price }} </v-card-text> -->
  </v-card>
</template>

<script>
export default {
  props: {
    Product: {
      type: Object,
      default: () => null,
    },
  },
  mounted: () => {
    console.log("resr");
    // console.log(this.Product);
  },

  data: () => {
    return {};
  },
};
</script>

<style></style>
