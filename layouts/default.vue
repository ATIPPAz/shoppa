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
              <v-btn v-show="!login" @click="Register()">
                register
                <v-icon> mdi-register </v-icon>
              </v-btn>
            </v-col>
            <v-col md="1.5">
              <v-btn @click="Logout" v-show="login">
                logout
                <v-icon> mdi-logout </v-icon>
              </v-btn>
              <v-btn @click="Login()" v-show="!login">
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
      <!-- <v-main class="grey lighten-4"> -->

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
      login: localStorage.getItem("AuthID") == null ? false : true,
    };
  },
  methods: {
    async Register() {
      this.login = !this.login;
      const res = await this.$axios.$post("user/Register", {
        name: "atip",
        username: "atippa",
      });
      console.log(res);
      //localStorage.setItem("authToken", token)  localStorage.getItem("userDetails");
      //:to="{ name: 'register' }
    },
    async Login() {
      this.login = !this.login;
      const res = await this.$axios.$post("user/Login", {
        username: "Atip",
        password: "1234",
      });
      if (res.length > 0) {
        res.forEach((element) => {
          localStorage.setItem("AuthID", element.CustID);
          localStorage.setItem("UserName", element.CustUsername);
        });
        this.$toast.success("Login Success");
      } else {
        this.$toast.error("Login failed");
      }
      //localStorage.setItem("authToken", token)  localStorage.getItem("userDetails");
      //:to="{ name: 'register' }
    },
    Logout() {
      localStorage.removeItem("AuthID");
      localStorage.removeItem("UserName");
      this.login = !this.login;
    },
  },
};
</script>
