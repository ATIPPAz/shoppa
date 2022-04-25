<template>
  <v-card>
    <v-card-title> {{ ProductData.name }} </v-card-title>
    <v-img :src="ProductData.url" aspect-ratio="1.5" contain></v-img>
    <v-card-text>
      ราคา : {{ ProductData.price }} มีจำนวน :
      {{ ProductData.qty }}</v-card-text
    >
    <v-card-text> {{ ProductData.discription }} </v-card-text>
    <v-btn>ซื้อเลย</v-btn>
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

  data: () => {
    return {};
  },
  mounted() {
    console.log(this.ProductData);
  },
};
</script>

<style></style>
