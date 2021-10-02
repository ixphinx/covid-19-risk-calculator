<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button color="primary"></ion-menu-button>
        </ion-buttons>
        <ion-title>{{ $route.params.id }}</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">{{ $route.params.id }}</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container" v-if="$route.params.id == 'Inicio'">
        <!--// INICIO //-->
        <ion-card v-if="login">
          <ion-card-header>
            <ion-card-title>Login</ion-card-title>
          </ion-card-header>

          <ion-card-content>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >User / email</span
              >
              <input
                type="text"
                class="form-control"
                aria-label="User / email"
                aria-describedby="inputGroup-sizing-sm"
                v-model="lgUser"
              />
            </div>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >Password</span
              >
              <input
                type="password"
                class="form-control"
                aria-label="Password"
                aria-describedby="inputGroup-sizing-sm"
                v-model="lgPassword"
              />
            </div>
            <button class="btn btn-primary btn-sm" @click="fnLogin()">
              Login
            </button>
            <a class="register" @click="(formRegistro = true), (login = false)"
              >Register</a
            >

            <div
              class="alert alert-danger"
              role="alert"
              style="margin-top: 1%"
              v-if="lgNotFound"
            >
              Usuario / email no encontrado.
            </div>
          </ion-card-content>
        </ion-card>
        <ion-card v-if="formRegistro">
          <ion-card-header>
            <ion-card-title>Register</ion-card-title>
          </ion-card-header>

          <ion-card-content>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >Name</span
              >
              <input
                type="text"
                class="form-control"
                aria-label="User / email"
                aria-describedby="inputGroup-sizing-sm"
                v-model="rgName"
              />
            </div>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >Lastname</span
              >
              <input
                type="text"
                class="form-control"
                aria-label="User / email"
                aria-describedby="inputGroup-sizing-sm"
                v-model="rgLastName"
              />
            </div>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >Age</span
              >
              <input
                type="text"
                class="form-control"
                aria-label="User / email"
                aria-describedby="inputGroup-sizing-sm"
                v-model="rgAge"
              />
            </div>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >Country</span
              >
              <input
                type="text"
                class="form-control"
                aria-label="User / email"
                aria-describedby="inputGroup-sizing-sm"
                v-model="rgContry"
              />
            </div>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >User</span
              >
              <input
                type="text"
                class="form-control"
                aria-label="User / email"
                aria-describedby="inputGroup-sizing-sm"
                v-model="rgUser"
              />
            </div>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >Password</span
              >
              <input
                type="password"
                class="form-control"
                aria-label="Password"
                aria-describedby="inputGroup-sizing-sm"
                v-model="rgPassword"
              />
            </div>
            <div class="input-group input-group-sm mb-3">
              <span class="input-group-text" id="inputGroup-sizing-sm"
                >Re-Password</span
              >
              <input
                type="password"
                class="form-control"
                aria-label="Password"
                aria-describedby="inputGroup-sizing-sm"
                v-model="rgRePassword"
              />
            </div>
            <div class="form-check">
              <input
                class="form-check-input"
                type="checkbox"
                value=""
                id="invalidCheck"
                @change="fnTermChek()"
              />
              <label class="form-check-label" for="invalidCheck">
                Agree to terms and conditions
              </label>
            </div>
            <button class="btn btn-primary btn-sm" @click="fnRegister()">
              Register
            </button>

            <div
              class="alert alert-success"
              role="alert"
              style="margin-top: 1%"
              v-if="success1"
            >
              User created successfully
            </div>
            <div
              class="alert alert-danger"
              role="alert"
              style="margin-top: 1%"
              v-if="fail1"
            >
              Passwords are diferent.
            </div>
            <div
              class="alert alert-danger"
              role="alert"
              style="margin-top: 1%"
              v-if="fail2"
            >
              All the fields must be completed.
            </div>
            <div
              class="alert alert-danger"
              role="alert"
              style="margin-top: 1%"
              v-if="fail3"
            >
              Agree the terms and conditions.
            </div>
          </ion-card-content>
        </ion-card>
      </div>

      <div id="container" v-if="$route.params.id == 'Usuario'">
        <!--// USUARIO //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Estadisticas'">
        <!--// ESTADISTICAS //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Previsiones'">
        <!--// PREVISIONES //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Riesgo'">
        <!--// CALCULO DE RIESGO //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Configuracion'">
        <!--// CONFIGURACIONES //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <!--// BOTON FLOTANTE //-->
      <ion-fab vertical="bottom" horizontal="end" slot="fixed">
        <ion-fab-button color="dark" @click="$router.push('Home')">
          <i class="fas fa-home"></i>
        </ion-fab-button>
      </ion-fab>
      <!--// BOTON FLOTANTE END //-->
    </ion-content>
  </ion-page>
</template>

<script>
import axios from "axios";

import {
  IonButtons,
  IonContent,
  IonHeader,
  IonMenuButton,
  IonPage,
  IonTitle,
  IonToolbar,
} from "@ionic/vue";

class Data {
  constructor(
    name,
    lastname,
    age,
    city,
    country,
    email,
    user,
    password,
    riskscore
  ) {
    this.name = name;
    this.lastname = lastname;
    this.age = age;
    this.city = city;
    this.country = country;
    this.email = email;
    this.user = user;
    this.password = password;
    this.riskscore = riskscore;
  }
}

export default {
  name: "Folder",
  components: {
    IonButtons,
    IonContent,
    IonHeader,
    IonMenuButton,
    IonPage,
    IonTitle,
    IonToolbar,
  },

  data() {
    return {
      datos: [],
      api: "https://covidcalculator.herokuapp.com/api",
      push: false,
      data: new Data(),

      //User data
      userData: [],
      chkUser: false,

      //Login Form
      lgUser: "",
      lgPassword: "",
      lgNotFound: false,
      login: true,

      //Register Form
      formRegistro: false,
      rgName: "",
      rgLastName: "",
      rgAge: "",
      rgContry: "",
      rgUser: "",
      rgPassword: "",
      rgRePassword: "",
      rgTermChek: false,

      //Health Form

      //Loaders
      mainLoader: false,
      loader1: false,

      //Success
      success1: false,

      //Fails
      fail1: false,
      fail2: false,
      fail3: false,
    };
  },

  created() {
    this.load();
  },

  methods: {
    load() {
      axios.get(this.api).then((res) => {
        this.datos = res.data;
      });
    },

    fnLogin() {
      let user = "";

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.user == this.lgUser || element.email == this.lgUser) {
          console.log("usuario encontrado");
          user = element.user;
        }
      }
    },

    fnTermChek(){
      if (this.rgTermChek){
        this.rgTermChek = false;
      } else {
        this.rgTermChek = true;
      }
    },

    fnRegister() {
      let chek = false;
      let chek2 = false;
      let chek3 = false;
      this.fail1 = false;
      this.fail2 = false;
      this.fail3 = false;
      this.loader1 = true;

      if (this.rgTermChek){
        chek3 = true;
      }

      if (this.rgPassword === this.rgRePassword) {
        chek = true;
      } else {
        this.fail1 = true;
      }

      if (
        this.rgName != "" &&
        this.rgLastName != "" &&
        this.rgAge != "" &&
        this.rgContry != "" &&
        this.rgUser != "" &&
        this.rgPassword != ""
      ) {
        chek2 = true;
      } else {
        this.fail2 = true;
      }

      if (!this.rgTermChek) {
        this.fail3 = true;
      }

      if (chek && chek2 && chek3) {
        this.data = new Data();
        this.data.name = this.rgName;
        this.data.lastname = this.rgLastName;
        this.data.age = this.rgAge;
        this.data.country = this.rgContry;
        this.data.user = this.rgUser;
        this.data.password = this.rgPassword;

        axios.post(this.api, this.data).then((res) => {
          console.log(res);

          axios.get(this.api).then((res) => {
            this.datos = res.data;
            this.loader1 = false;
            this.success1 = true;

            this.rgName = "";
            this.rgLastName = "";
            this.rgAge = "";
            this.rgContry = "";
            this.rgUser = "";
            this.rgPassword = "";
          });
        });
      }
    },
  },
};
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
}

#container a {
  text-decoration: none;
}

.register {
  margin-left: 20%;
  font-size: 80%;
  color: #098ae6;
}
</style>