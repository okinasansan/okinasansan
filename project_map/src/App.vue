<template>
  <v-app>
    <v-app-bar elevation="2">
      <RouterLink to="/about">About</RouterLink>
    </v-app-bar>
    <v-main>
      <v-card
      max-width="10000"
      >
        <v-img
        height="250"
        src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
        ></v-img>

        <v-card-title>電大カフェ</v-card-title>
        <v-card-text>
          <div class="my-4 text-subtitle-1">
            作品：東京電機大学
          </div>
          <div class="my-4 text-subtitle-1">
            〒120-8551 東京都足立区千住旭町５
          </div>
          <div>Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating.</div>
        </v-card-text>
      </v-card>
      <div>
        <div class="map" ref="googleMap" />
      </div>

      <div>
        ルートを表示
      </div>
    </v-main>

    <v-footer
      color="primary lighten-1"
      padless
    >
      <v-row
        justify="center"
        no-gutters
      >
        <v-col
          class="primary lighten-2 py-4 text-center white--text"
          cols="12"
        >
          {{ new Date().getFullYear() }} — <strong>情報通信プロジェクト</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
  
</template>

<script>
import GoogleMapsApiLoader from 'google-maps-api-loader';
import { RouterLink, RouterView } from 'vue-router'

export default {
  name: 'Map',
  data() {
    return {
      google: null,
      mapConfig: {
        center: {
          lat: 35.74861780559465, 
          lng: 139.80627656294405
        },
        zoom: 17
      }
    }
  },
  async mounted() {
    this.google = await GoogleMapsApiLoader({
      apiKey: 'AIzaSyB6PSkvWZX2a3x96hmrjJIbnZGDQwhkC6I'
    });
    this.initializeMap();
  },
  methods: {
    initializeMap() {
      new this.google.maps.Map(this.$refs.googleMap, this.mapConfig);
    }
  }
}
</script>

<style lang="scss" scoped>
.map {
  width: 80vw;
  height: 50vh;
}
</style>