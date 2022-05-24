<template>
  <v-card class="pa-2" outlined tile>
    <router-link
      :to="{
        name: 'ProductDetail-slug',
        params: { slug: ProductData },
      }"
    >
      <v-img
        :lazy-src="ProductData.ProdImage"
        aspect-ratio="1"
        class="grey lighten-2"
        :src="ProductData.ProdImage"
        height="200px"
      >
      </v-img>
    </router-link>

    <v-card-title>
      {{ ProductData.ProdName }}
    </v-card-title>

    <v-card-text>
      ราคา : {{ ProductData.ProdPrice }} <v-spacer /> มีจำนวน :{{
        ProductData.ProdQty
      }}</v-card-text
    >
    <v-card-actions>
      <v-btn
        :loading="loading"
        @click="Buy(ProductData)"
        rounded
        outlined
        small
        align-self="end"
        :disabled="ProductData.ProdQty <= 0"
      >
        <v-icon v-show="ProductData.ProdQty > 0">mdi-cart</v-icon
        >{{ ProductData.ProdQty > 0 ? "Buy" : "Sold Out" }}
      </v-btn>
      <v-spacer></v-spacer>
      รายละเอียดสินค้า
      <v-btn icon @click="show = !show">
        <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
      </v-btn>
    </v-card-actions>
    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          {{ ProductData.ProdDest }}
        </v-card-text>
      </div>
    </v-expand-transition>
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
    return {
      loading: false,
      show: false,
    };
  },
  mounted() {
    console.log(this.ProductData);
  },
  methods: {
    async Buy(item) {
      if (item.ProdQty <= 0) {
        this.$toast.error("สินค้าหมดเเล้ว");
        return;
      }
      this.loading = true;
      this.$toast.success("กำลังจัดซื้อ");
      await setTimeout(() => {
        this.loading = false;
        item.ProdQty = item.ProdQty - 1;
        this.$toast.success("ซื้อเเล้ว");
      }, 5000);
    },
    OpenDetail(item) {
      console.log("click");
      console.warn(item);
      this.$router.push({
        path: "/Products/productDetail",
      });
      lacalStorage.setItem("productDetail", JSON.stringify(item));
    },
  },
};
</script>

<style></style>
