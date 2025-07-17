<script setup>
import { ref } from 'vue'
import LogoCSUCC from '@/assets/logo/Csucc.png'
import BcCSUCC from '@/assets/logo/bccsucc.png'
import WebLogo from '@/assets/logo/weblogo.png'

const theme = ref('light')

function onClick() {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}
</script>

<template>
  <v-responsive>
    <v-app :theme="theme">
      <v-app-bar class="px-3">
        <v-spacer></v-spacer>
        <div class="top-left">
          <v-img :src="WebLogo" width="200" height="auto" class="logo"></v-img>
        </div>

        <v-btn
          :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          slim
          @click="onClick"
        ></v-btn>
      </v-app-bar>
      <v-main
        :style="{
          backgroundImage: `url(${BcCSUCC})`,
          backgroundSize: 'cover',
          backgroundPosition: 'center',
          minHeight: '100vh',
        }"
      >
        <v-container>
          <v-row>
            <v-col cols="12" class="d-flex flex-column align-center justidfy-center">
              <v-img :src="LogoCSUCC" contain width="200" height="200"> </v-img>
              <h1 class="text-h2 text-center mt-16 font_weight-bold">
                Welcome to CSU-CC Home Page
              </h1>
              <v-btn
                class="mt-5"
                prepend-icon="mdi-login"
                size="x-large"
                color="green"
                elevation="10"
                to="login"
              >
                Login Here!
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-main>
    </v-app>
  </v-responsive>
</template>

<style scoped>
.top-left {
  position: absolute;
  top: 0px;
  left: 2px;
  display: flex;
  align-items: center;
  padding: 0.5rem;
  gap: 0.5rem;
}
h1 {
  color: white;
}
</style>
