<template>
  <v-card>
    <v-img
      :lazy-src="ProductData.ProdImage"
      aspect-ratio="1"
      class="grey lighten-2"
      :src="ProductData.ProdImage"
      height="200px"
      @click.stop="OpenDetail(ProductData)"
    >
    </v-img>
    <v-card-title @click.stop="OpenDetail(ProductData)">
      {{ ProductData.ProdName }}
    </v-card-title>

    <v-card-text @click.stop="OpenDetail(ProductData)">
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
      productUrl:
        "https://drive.google.com/uc?export=view&id=1H2PKMba4KDO10XQCQl-g9GZyEOoSAbcs",
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
      this.$router.push({
        path: "/Products/productDetail",
        params: item,
      });
    },
  },
};
</script>

<style></style>
