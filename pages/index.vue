<template>
  <v-flex>
    <v-card>
      <v-card-title> แบรนด์ </v-card-title>
    </v-card>
    <v-flex>
      <v-container>
        <v-row>
          <v-col sm="3" v-for="item in Products" :key="item.id">
            <ProductsProductCard @click="OpenDetail" :ProductData="item" />
          </v-col>
        </v-row>
      </v-container>
    </v-flex>
    <v-card>
      <v-card-title> ประเภท </v-card-title>
    </v-card>
    <v-flex>
      <v-container>
        <v-row>
          <v-col sm="3" v-for="item in Products" :key="item.id">
            <ProductsProductCard @click="OpenDetail" :ProductData="item" />
          </v-col>
        </v-row>
      </v-container>
    </v-flex>
    <v-card> </v-card>
    <v-card>
      <v-card-title> สินค้าแนะนำ </v-card-title>
    </v-card>
    <v-flex>
      <v-container>
        <v-row>
          <v-col sm="3" v-for="item in Products" :key="item.id">
            <ProductsProductCard :ProductData="item" />
          </v-col>
        </v-row>
      </v-container>
    </v-flex>
  </v-flex>
</template>

<script>
export default {
  name: "IndexPage",
  data: () => {
    return {
      Products: [
        {
          id: 1,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 5,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 2,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 1,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 3,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 254,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 4,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 254,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 5,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 254,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 6,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 254,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 7,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 254,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 8,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 254,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 9,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 254,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
        {
          id: 10,
          name: "Iphone 18",
          url: "https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/iphone-12-family-select-2021?wid=940&hei=1112&fmt=jpeg&qlt=90&.v=1617135051000",
          price: 32000,
          qty: 254,
          discription: "ราคาถูกที่สุด ใช้ง่าย ใช้ดี",
        },
      ],
    };
  },
  methods: {},
};
</script>
