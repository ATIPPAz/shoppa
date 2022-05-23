<template>
  <v-flex>
    <ReceiptDetail :id="slug" />
  </v-flex>
</template>

<script>
export default {
  asyncData({ params }) {
    const slug = parseInt(params.slug);
    return { slug };
  },

  head() {
    return {
      title: "Receipt Information",
    };
  },
};
</script>
//
<router-link
  :to="{ name: 'warehouse-receipt-slug', params: { slug: parseInt(item.id) } }"
>
//               <v-btn color="primary" :disabled="loading" small>
//                 เพิ่มเติม
//               </v-btn>
//             </router-link>
