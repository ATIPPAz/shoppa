<template>
  <v-flex>
    <v-container>
      <v-row no-gutters class="pl-5 pt-5 pb-5 pr-5 grey lighten-5">
        <v-col cols="12" sm="4">
          <v-card class="pa-2 mr-5" outlined tile>
            <v-img
              :lazy-src="Product.ProdImage"
              aspect-ratio="1"
              class="grey lighten-2 fill-height"
              :src="Product.ProdImage"
            >
            </v-img>
          </v-card>
        </v-col>
        <v-col cols="12" sm="8">
          <v-card class="pa-2 ml-5" height="100%" outlined tile>
            <v-card-title>
              {{ Product.ProdName }}
            </v-card-title>
            <v-card-subtitle>
              {{ Product.ProdDest }}
            </v-card-subtitle>
            <v-flex class="grey lighten-2">
              มีจำนวน {{ Product.ProdQty }} <br />
              ราคา{{ Product.ProdPrice }}</v-flex
            >
            <v-card-actions>
              <v-btn
                color="primary"
                class="white--text"
                dark
                text
                @click="addToCart(Product)"
              >
                เพิ่มในตะกร้า
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
      <v-row class="pr-2 mt-5 grey lighten-5" no-gutters>
        <v-card class="pa-2 mr-5" outlined tile> สินค้าคล้ายกัน </v-card>
      </v-row>
    </v-container>
    <!-- <v-card>
      <v-img
        :lazy-src="Product.ProdImage"
        aspect-ratio="1"
        class="grey lighten-2"
        :src="Product.ProdImage"
        height="1000px"
      >
      </v-img>
      <v-card-title>{{ Product.ProdName }}</v-card-title>
    </v-card> -->
  </v-flex>
</template>

<script>
export default {
  props: {
    Products: {
      type: Object,
      default: () => null,
    },
  },
  mounted() {
    this.GetDetail();
  },

  data: () => {
    return {
      Product: [],
      cart: [],
    };
  },
  methods: {
    log: function (evt) {
      console.log(evt);
      if (!evt.added) {
        console.log("ไม่ได้ใส่");
        return;
      }
    },
    async GetDetail() {
      console.log(this.Product.ProdID);
      const res = await this.$axios.$post("/FindOneProduct", {
        ProID: this.Products.ProdID,
      });
      this.Product = res[0];
      console.warn(res);
    },
  },
  head() {
    return {
      title: "ProductDetail",
    };
  },
};
</script>

<style></style>
