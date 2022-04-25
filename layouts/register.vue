<template>
  <v-app>
    <div class="d-flex text-center flex-column flex-md-row flex-grow-1">
      <v-sheet
        class="layout-side mx-auto mx-md-1 d-none d-md-flex flex-md-column justify-space-between px-2"
      >
        <div class="mt-3 mt-md-10 pa-2">
          <div class="display-2 font-weight-bold error--text">Kaizen</div>
          <div class="title my-2">We are the best of Manager</div>
        </div>
        <img
          class="w-full"
          src="/images/illustrations/signin-illustration.svg"
        />
      </v-sheet>

      <div
        class="pa-2 pa-md-4 flex-grow-1 align-center justify-center d-flex flex-column"
      >
        <div class="layout-content ma-auto w-full">
          <Nuxt />
        </div>
        <div class="overline mt-4">kaizen-1.0.0</div>
      </div>
    </div>
    <Footer />
  </v-app>
</template>
<style scoped>
.layout-side {
  width: 420px;
}
.layout-content {
  max-width: 480px;
}
</style>
