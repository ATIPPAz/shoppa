<template>
  <v-flex>
    <productDetail :Products="slug" />
  </v-flex>
</template>

<script>
import productDetail from "../Products/productDetail.vue";
export default {
  components: { productDetail },
  asyncData({ params }) {
    const slug = params.slug;
    return { slug };
  },

  head() {
    return {
      title: "Receipt Information",
    };
  },
};
</script>
