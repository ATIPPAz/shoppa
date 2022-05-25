<template>
  <v-card class="pa-2" outlined tile>
    <router-link
      :to="{
        name: 'ProductDetail-slug',
        params: { slug: ProductData },
      }"
    >
      <v-img
        :lazy-src="NoImg"
        aspect-ratio="1"
        :src="ProductData.ProdImage ? ProductData.ProdImage : NoImg"
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
        @click="Buy()"
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
      NoImg:
        "data:image/png;base64,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",
    };
  },
  mounted() {},
  methods: {
    async Buy() {
      if (localStorage.getItem("AuthID") === null) {
        this.$toast.error("กรุณาเข้าสู่ระบบก่อน");
        return;
      }
      this.loading = true;
      const qty = 1;
      const cost = parseInt(this.ProductData.ProdPrice) * qty;
      this.Opendialog = false;
      const getBank = await this.$axios.$post("Customers/GetBankAccount");
      const custID = localStorage.getItem("AuthID");
      const CustBank = getBank.filter((bank) => bank.CustID === custID);
      const resPurchase = await this.$axios.$post("/Purchase", {
        BankID: CustBank[0].BankNumber,
        Cost: cost,
      });
      await setTimeout(async () => {
        if (resPurchase) {
          const res = await this.$axios.$post("/Order", {
            CustID: custID,
            CreateDate: `${new Date().toISOString().slice(0, 10)}`,
            ShipID: "SP02",
            OrderStatus: "OS02",
            Annotation: "test buy",
            ProdID: this.ProductData.ProdID,
            ProdQty: parseInt(qty),
            ProdCost: 5,
            ProdPrice: parseInt(this.ProductData.ProdPrice),
          });
          this.$toast.success("ซื้อสินค้าเรียบร้อย กำลังจัดทำออเดอร์ . . .");
          this.ProductData.ProdQty -= 1;
          await setTimeout(async () => {
            if (res) {
              this.$toast.success("ทำออเดอร์เรียบร้อย");
            } else {
              this.$toast.error("เกิดข้อผิดพลาด งั้นขอเงินไปก่อนนะครับ");
            }
            this.loading = false;
          }, 1500);
        } else {
          this.$toast.error("ซื้อสินค้าไม่ได้ เนื่องจากเงินไม่พอ");
          this.loading = false;
        }
      }, 1500);

      //const makeOrder = await this.$axios.post();
      //const DateBuy = new Date().toISOString().slice(0, 10);
    },
  },
};
</script>

<style></style>
