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
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <ion-card>
          <ion-card-header>
            <ion-card-title>Login</ion-card-title>
          </ion-card-header>

          <ion-card-content>
            
          </ion-card-content>
        </ion-card>
        <!--// CONTENIDO AQUI XD //-->
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
    };
  },

  created() {
    this.load();
    axios.get(this.api).then((res) => {
      this.datos = res.data;
    });
  },

  methods: {
    load() {
      this.datos = [];
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
</style>