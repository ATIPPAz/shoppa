<template>
  <v-app>
    <v-app-bar class="indigo darken-2" fixed app>
      <v-container>
        <v-row no-gutters class="pl-16">
          <v-col cols="12" class="d-flex" sm="4">
            <v-flex class="align-self-center">
              <p class="font-weight-black pl-2 white--text my-auto">Shoppa¥</p>
            </v-flex>
          </v-col>
          <v-col cols="12" sm="4"> </v-col>
          <v-col cols="12" class="d-flex" sm="4">
            <v-flex class="d-flex">
              <v-flex class="d-flex flex-row-reverse mr-16">
                <v-btn
                  outlined
                  rounded
                  class="mr-2 white--text"
                  v-show="!login"
                  @click="DialogRegister = true"
                >
                  register
                  <v-icon> mdi-register </v-icon>
                </v-btn>

                <v-btn
                  outlined
                  class="mr-2 white--text"
                  rounded
                  @click="Logout"
                  v-show="login"
                >
                  logout
                  <v-icon> mdi-logout </v-icon>
                </v-btn>
                <v-btn
                  outlined
                  class="mr-2 white--text"
                  rounded
                  @click="DialogLogin = true"
                  v-show="!login"
                >
                  login
                  <v-icon> mdi-login </v-icon>
                </v-btn>
              </v-flex>
            </v-flex>
          </v-col>
        </v-row>
      </v-container>
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
    <v-dialog v-model="DialogLogin" max-width="500" persistent>
      <v-card class="pa-5">
        <v-card elevation="0">
          <v-card-title class="pa-0 pb-5"> Login To Yabep</v-card-title>
        </v-card>
        <v-form ref="formLogin" v-model="valid" lazy-validation>
          <v-text-field
            outlined
            v-model="username"
            :counter="10"
            :rules="nameRules"
            label="Name"
            required
          ></v-text-field>

          <v-text-field
            v-model="password"
            outlined
            :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
            :type="show1 ? 'text' : 'password'"
            :items="items"
            :rules="[(v) => !!v || 'Item is required']"
            label="Password"
            required
          ></v-text-field>
          <v-card-actions class="ma-0 pa-0 d-flex flex-row-reverse">
            <v-btn
              :disabled="!valid"
              color="success"
              class="ma-0"
              @click="Login()"
            >
              Login
            </v-btn>

            <v-btn color="error" class="mr-3" @click="DialogLogin = false">
              close
            </v-btn>
          </v-card-actions>
        </v-form></v-card
      >
    </v-dialog>
    <v-dialog v-model="DialogRegister" max-width="500" persistent>
      <v-card class="pa-5">
        <v-form ref="form" v-model="valid" lazy-validation>
          <v-container fluid>
            <v-row align="center">
              <v-col cols="6"
                ><v-text-field
                  v-model="username"
                  :rules="nameRules"
                  label="UserName"
                  required
                ></v-text-field
              ></v-col>
              <v-col cols="6"
                ><v-text-field
                  v-model="password"
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :type="show1 ? 'text' : 'password'"
                  :rules="[(v) => !!v || 'Item is required']"
                  label="Password"
                  required
                ></v-text-field
              ></v-col>
            </v-row>

            <v-row align="center">
              <v-col cols="6">
                <v-text-field
                  v-model="firstname"
                  :rules="nameRules"
                  label="FirstName"
                  required
                ></v-text-field
              ></v-col>
              <v-col cols="6">
                <v-text-field
                  v-model="Lastname"
                  :rules="nameRules"
                  label="Lastname"
                  required
                ></v-text-field
              ></v-col>
            </v-row>
          </v-container>

          <v-container fluid>
            <v-row align="center">
              <v-col cols="6">
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="E-mail"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="6">
                <v-card elevation="0">
                  <v-menu
                    ref="menu1"
                    v-model="menu1"
                    :close-on-content-click="false"
                    transition="scale-transition"
                    offset-y
                    max-width="290px"
                    min-width="auto"
                  >
                    <template v-slot:activator="{ on, attrs }">
                      <v-text-field
                        v-model="dateFormatted"
                        label="Date"
                        hint="MM/DD/YYYY format"
                        persistent-hint
                        prepend-icon="mdi-calendar"
                        v-bind="attrs"
                        @blur="date = parseDate(dateFormatted)"
                        v-on="on"
                      ></v-text-field>
                    </template>
                    <v-date-picker
                      v-model="date"
                      no-title
                      @input="menu1 = false"
                    ></v-date-picker>
                  </v-menu> </v-card
              ></v-col>
            </v-row>
          </v-container>
          <v-container fluid>
            <v-row align="center">
              <v-col cols="6">
                <v-text-field
                  v-model="Phone"
                  :rules="{
                    required: true,
                    digits: 7,
                    regex: '^(71|72|74|76|81|82|84|85|86|87|88|89)\\d{5}$',
                  }"
                  label="TelePhone"
                  required
                >
                </v-text-field>
              </v-col>
              <v-col cols="6">
                <v-select v-model="gender" :items="genderitem" label="Gerder">
                </v-select>
              </v-col>
            </v-row>
          </v-container>

          <v-card-actions class="ma-0 pa-0 d-flex flex-row-reverse">
            <v-btn
              :disabled="!valid"
              color="success"
              class="mr-4"
              @click="Register()"
            >
              Done
            </v-btn>
            <v-btn color="error" class="mr-4" @click="DialogRegister = false">
              Close
            </v-btn>
          </v-card-actions>
        </v-form></v-card
      >
    </v-dialog>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data: () => {
    return {
      login: localStorage.getItem("AuthID") == null ? false : true,
      DialogLogin: false,
      DialogRegister: false,
      valid: true,
      username: "",
      password: "",
      genderitem: ["male", "female"],
      show1: false,
      name: "",
      nameRules: [
        (v) => !!v || "Name is required",
        (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
      ],
      email: "",
      emailRules: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
      ],
      select: null,
      items: ["Item 1", "Item 2", "Item 3", "Item 4"],
      checkbox: false,
    };
  },
  methods: {
    async Register() {
      this.DialogRegister = false;
      // this.login = !this.login;
      // const res = await this.$axios.$post("user/Register", {
      //   name: "atip",
      //   username: "atippa",
      // });
      // console.log(res);
      //localStorage.setItem("authToken", token)  localStorage.getItem("userDetails");
      //:to="{ name: 'register' }
    },
    validate() {
      this.$refs.form.validate();
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    },
    async Login() {
      const res = await this.$axios.$post("user/Login", {
        username: this.username,
        password: this.password,
      });
      if (res.length > 0) {
        res.forEach((element) => {
          localStorage.setItem("AuthID", element.CustID);
          localStorage.setItem("UserName", element.CustUsername);
        });
        this.Username = "";
        this.Password = "";
        this.login = !this.login;
        this.DialogLogin = false;
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
