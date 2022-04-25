<template>
  <v-card>
    <v-card-title> {{ ProductData.name }} </v-card-title>
    <v-img :src="ProductData.url" aspect-ratio="1.5" contain></v-img>
    <v-card-text>
      ราคา : {{ ProductData.price }} มีจำนวน :
      {{ ProductData.qty }}</v-card-text
    >
    <v-card-text> {{ ProductData.discription }} </v-card-text>
    <v-card-actions>
      <v-btn @click="Buy" rounded outlined small class="left">
        <v-icon>mdi-cart</v-icon>Buy
      </v-btn>
    </v-card-actions>
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
  methods: {
    Buy() {
      $toast.success("ซื้อเเล้ว");
    },
  },
};
</script>

<style></style>
