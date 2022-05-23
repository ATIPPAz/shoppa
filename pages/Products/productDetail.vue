<template>
  <v-card>
    <div class="row">
      <div class="col-3">
        <h3>Draggable 1</h3>
        <draggable
          class="dragArea list-group"
          :list="Products"
          :group="{ name: 'people', pull: 'clone', put: false }"
          :clone="cloneDog"
          @change="log"
        >
          <div
            class="list-group-item"
            v-for="element in Products"
            :key="element.id"
          >
            <ProductsProductCard :ProductData="element" />
          </div>
        </draggable>
      </div>

      <div class="col-3">
        <h3>Draggable 2</h3>
        <draggable
          class="dragArea list-group"
          :list="cart"
          group="people"
          @change="log"
        >
          <div
            class="list-group-item"
            v-for="element in cart"
            :key="element.id"
          >
            <div v-if="element">
              <ProductsProductCard :ProductData="element" />
            </div>
          </div>
        </draggable>
      </div>
    </div>
  </v-card>
</template>

<script>
export default {
  components: {
    draggable,
  },
  props: {
    Product: {
      type: Object,
      default: () => null,
    },
  },
  mounted: () => {
    window.console.log("resr");
    // console.log(this.Product);
  },

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

    cloneDog(prop) {
      console.log(this.cart);
      console.log(this.Products);
      console.log(prop);
      let canadd = true;
      if (!(prop.qty <= 0)) {
        this.cart.map((item) => {
          if (item.id === prop.id) {
            item.qty += 1;
            prop.qty -= 1;
            canadd = false;
          }
        });
        if (canadd) {
          prop.qty -= 1;
          return {
            id: prop.id,
            name: prop.name,
            url: prop.url,
            price: prop.price,
            qty: 1,
            discription: prop.discription,
          };
        }
      }
    },
  },
  head() {
    return {
      title: "Receipt",
    };
  },
};
</script>

<style></style>
<router-link
  :to="{ name: 'warehouse-receipt-slug', params: { slug: parseInt(item.id) } }"
>
              <v-btn color="primary" :disabled="loading" small>
                เพิ่มเติม
              </v-btn>
            </router-link>
