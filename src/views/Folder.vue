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

      <div id="container" v-if="$route.params.id == 'Main'">
        <!--// INICIO //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Home'">
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
              User / email not found.
            </div>
            <div
              class="alert alert-danger"
              role="alert"
              style="margin-top: 1%"
              v-if="lgNotFound2"
            >
              Incorrect password.
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
              Registred successfully!
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
        <ion-card v-if="formHealth">
          <ion-card-header>
            <ion-card-title>Health</ion-card-title>
          </ion-card-header>

          <ion-card-content>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="stds"
                  @click="fnSelect('stds')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - STDs
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="cancer"
                  @click="fnSelect('cancer')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Cancer
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="mobesity"
                  @click="fnSelect('mobesity')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Morbid obesity
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="diabetes"
                  @click="fnSelect('diabetes')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Diabetes
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="hypertension"
                  @click="fnSelect('hypertension')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Hypertension
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="asthma"
                  @click="fnSelect('asthma')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Asthma
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="pneumonia"
                  @click="fnSelect('pneumonia')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Pneumonia
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="allergy"
                  @click="fnSelect('allergy')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Allergy
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="hattack"
                  @click="fnSelect('hattack')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Having suffered a heart attack.
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="surgeries"
                  @click="fnSelect('surgeries')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Have undergone surgeries
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="vaccinated"
                  @click="fnSelect('vaccinated')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - Vaccinated
                </label>
              </div>
            </div>
            <div class="col-12" style="text-align: left">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="checkbox"
                  value=""
                  id="invalidCheck"
                  v-model="noneotl"
                  @click="fnSelect('noneotl')"
                />
                <label class="form-check-label" for="invalidCheck">
                  - None of the list.
                </label>
              </div>
            </div>
            <button class="btn btn-primary btn-sm" @click="fnHealth()">
              <img
                src="assets/img/loader.gif"
                width="15"
                alt=""
                v-if="loader2"
              />
              Save
            </button>

            <div
              class="alert alert-success"
              role="alert"
              style="margin-top: 1%"
              v-if="success2"
            >
              Data saved!
            </div>
          </ion-card-content>
        </ion-card>
        <ion-card v-if="status">
          <ion-card-header>
            <ion-card-title>Status</ion-card-title>
          </ion-card-header>

          <ion-card-content> </ion-card-content>
        </ion-card>
      </div>

      <div id="container" v-if="$route.params.id == 'Profile'">
        <!--// USUARIO //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Statics'">
        <!--// ESTADISTICAS //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Forecasts'">
        <!--// PREVISIONES //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Risk'">
        <!--// CALCULO DE RIESGO //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <div id="container" v-if="$route.params.id == 'Settings'">
        <!--// CONFIGURACIONES //-->
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <!--// CONTENIDO AQUI XD //-->
      </div>

      <!--// BOTON FLOTANTE //-->
      <ion-fab vertical="bottom" horizontal="end" slot="fixed">
        <ion-fab-button
          color="dark"
          @click="
            $router.push('Home'),
              (login = true),
              (formHealth = false),
              (formRegistro = false)
          "
        >
          <i class="fas fa-home"></i>
        </ion-fab-button>
      </ion-fab>
      <!--// BOTON FLOTANTE END //-->
    </ion-content>
  </ion-page>
</template>

<script>
import axios from "axios";
import countries from "../json/countries.json";

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
    stds,
    cancer,
    mobesity,
    diabetes,
    hypertension,
    asthma,
    pneumonia,
    allergy,
    hattack,
    surgeries,
    vaccinated
  ) {
    this.name = name;
    this.lastname = lastname;
    this.age = age;
    this.city = city;
    this.country = country;
    this.email = email;
    this.user = user;
    this.password = password;
    this.stds = stds;
    this.cancer = cancer;
    this.mobesity = mobesity;
    this.diabetes = diabetes;
    this.hypertension = hypertension;
    this.asthma = asthma;
    this.pneumonia = pneumonia;
    this.allergy = allergy;
    this.hattack = hattack;
    this.surgeries = surgeries;
    this.vaccinated = vaccinated;
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
      loged: false,
      contries: countries,

      //Status
      status: false,

      //User data
      userData: [],
      chkUser: false,
      userId: "",

      //Login Form
      lgUser: "",
      lgPassword: "",
      lgNotFound: false,
      lgNotFound2: false,
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
      formHealth: false,
      stds: false,
      cancer: false,
      mobesity: false,
      diabetes: false,
      hypertension: false,
      asthma: false,
      pneumonia: false,
      allergy: false,
      hattack: false,
      surgeries: false,
      vaccinated: false,
      noneotl: false,

      //Loaders
      mainLoader: false,
      loader1: false,
      loader2: false,

      //Success
      success1: false,
      success2: false,

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
      let userId = "";
      this.lgNotFound = false;
      this.lgNotFound2 = false;
      this.userData = [];

      for (let i = 0; i < this.datos.length; i++) {
        const element = this.datos[i];
        if (element.user == this.lgUser || element.email == this.lgUser) {
          userId = element._id;
          break;
        }
      }

      if (userId == "") {
        this.lgNotFound = true;
      }

      if (userId != "") {
        for (let i = 0; i < this.datos.length; i++) {
          const element = this.datos[i];
          if (element._id == userId && element.password == this.lgPassword) {
            this.status = true;
            this.login = false;

            this.userData.push({
              id: element._id,
              name: element.name,
              lastname: element.lastname,
              age: element.age,
              city: element.city,
              country: element.country,
              email: element.email,
              user: element.user,
              password: element.password,
              stds: element.stds,
              cancer: element.cancer,
              mobesity: element.mobesity,
              diabetes: element.diabetes,
              hypertension: element.hypertension,
              asthma: element.asthma,
              pneumonia: element.pneumonia,
              allergy: element.allergy,
              hattack: element.hattack,
              surgeries: element.surgeries,
              vaccinated: element.vaccinated,
            });
            break;
          }

          if (element._id == userId && element.password != this.lgPassword) {
            this.lgNotFound2 = true;
            break;
          }
        }
      }
    },

    fnTermChek() {
      if (this.rgTermChek) {
        this.rgTermChek = false;
      } else {
        this.rgTermChek = true;
      }
    },

    fnRegister() {
      let user = "";
      let chek = false;
      let chek2 = false;
      let chek3 = false;
      this.fail1 = false;
      this.fail2 = false;
      this.fail3 = false;
      this.loader1 = true;

      if (this.rgTermChek) {
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
        user = this.rgUser;
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
            this.formRegistro = false;
            this.formHealth = true;

            for (let i = 0; i < this.datos.length; i++) {
              const element = this.datos[i];
              if (element.user == user) {
                this.userId = element._id;
                break;
              }
            }

            this.rgName = "";
            this.rgLastName = "";
            this.rgAge = "";
            this.rgContry = "";
            this.rgUser = "";
            this.rgPassword = "";
            this.rgRePassword = "";
          });
        });
      }
    },

    fnHealth() {
      this.loader2 = true;

      this.data = new Data();
      this.data.stds = this.stds;
      this.data.cancer = this.cancer;
      this.data.mobesity = this.mobesity;
      this.data.diabetes = this.diabetes;
      this.data.hypertension = this.hypertension;
      this.data.asthma = this.asthma;
      this.data.pneumonia = this.pneumonia;
      this.data.allergy = this.allergy;
      this.data.hattack = this.hattack;
      this.data.surgeries = this.surgeries;
      this.data.vaccinated = this.vaccinated;

      axios.put(this.api + "/" + this.userId, this.data).then((res) => {
        console.log(res);

        axios.get(this.api).then((res) => {
          this.datos = res.data;
          this.loader2 = false;
          this.success2 = true;
        });
      });
    },

    fnSelect(selection) {
      switch (selection) {
        case "stds":
          this.stds = true;
          this.noneotl = false;
          break;
        case "cancer":
          this.cancer = true;
          this.noneotl = false;
          break;
        case "mobesity":
          this.mobesity = true;
          this.noneotl = false;
          break;
        case "diabetes":
          this.diabetes = true;
          this.noneotl = false;
          break;
        case "hypertension":
          this.hypertension = true;
          this.noneotl = false;
          break;
        case "asthma":
          this.asthma = true;
          this.noneotl = false;
          break;
        case "pneumonia":
          this.pneumonia = true;
          this.noneotl = false;
          break;
        case "allergy":
          this.allergy = true;
          this.noneotl = false;
          break;
        case "hattack":
          this.hattack = true;
          this.noneotl = false;
          break;
        case "surgeries":
          this.surgeries = true;
          this.noneotl = false;
          break;
        case "vaccinated":
          this.vaccinated = true;
          this.noneotl = false;
          break;
        case "noneotl":
          this.noneotl = true;
          this.stds = false;
          this.cancer = false;
          this.mobesity = false;
          this.diabetes = false;
          this.hypertension = false;
          this.asthma = false;
          this.pneumonia = false;
          this.allergy = false;
          this.hattack = false;
          this.surgeries = false;
          this.vaccinated = false;
          break;
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