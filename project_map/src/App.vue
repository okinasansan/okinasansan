<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
      <v-toolbar-title>タイトル</v-toolbar-title>

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <v-sheet id="map"
      class="pa-0"
      :light="true"
      style="width: 100%; height: 300px;"
    >
      google map
  </v-sheet>

  <RouterView />
</template>


