<template>
  <v-app>
    <v-app-bar class="primary" fixed app>
      <v-row>
        <v-col md="2" sm="1"></v-col>
        <v-col md="8" sm="5">
          <v-row>
            <v-col md="2"> logo </v-col>
            <v-col md="7">
              <v-text-field />
            </v-col>
            <v-col md="1.5">
              <v-btn
                v-show="!login"
                @click="login = !login"
                :to="{ name: 'register' }"
              >
                register
                <v-icon> mdi-register </v-icon>
              </v-btn>
            </v-col>
            <v-col md="1.5">
              <v-btn @click="login = !login" v-show="login">
                logout
                <v-icon> mdi-logout </v-icon>
              </v-btn>
              <v-btn @click="login = !login" v-show="!login">
                login
                <v-icon> mdi-login </v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </v-col>
        <v-col md="2" sm="1"></v-col>
      </v-row>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-app class="my-2 mx-15">
          <Nuxt />
        </v-app>
      </v-container>

      <v-footer inset>
        <v-spacer />
        <div class="overline">
          Built with
          <v-icon small color="pink"> mdi-heart </v-icon>
          &copy; ATIPPA DEV {{ new Date().getFullYear() }}
        </div>
      </v-footer>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data: () => {
    return {
      login: false,
    };
  },
};
</script>
