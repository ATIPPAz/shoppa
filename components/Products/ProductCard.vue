<template>
  <v-card>
    <v-img
      :lazy-src="ProductData.url"
      aspect-ratio="1"
      class="grey lighten-2"
      :src="ProductData.url"
      height="200px"
      @click.stop="OpenDetail(ProductData)"
    >
    </v-img>
    <v-card-title @click.stop="OpenDetail(ProductData)">
      {{ ProductData.name }}
    </v-card-title>

    <v-card-text @click.stop="OpenDetail(ProductData)">
      ราคา : {{ ProductData.price }} <v-spacer /> มีจำนวน :{{
        ProductData.qty
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
        :disabled="ProductData.qty <= 0"
      >
        <v-icon v-show="ProductData.qty > 0">mdi-cart</v-icon
        >{{ ProductData.qty > 0 ? "Buy" : "Sold Out" }}
      </v-btn>
      <v-spacer></v-spacer>

      <v-btn icon @click="show = !show">
        <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
      </v-btn>
    </v-card-actions>
    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          {{ ProductData.discription }}
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
      if (item.qty <= 0) {
        this.$toast.error("สินค้าหมดเเล้ว");
        return;
      }
      this.loading = true;
      this.$toast.success("กำลังจัดซื้อ");
      await setTimeout(() => {
        this.loading = false;
        item.qty = item.qty - 1;
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
