<script setup>
import { ref } from 'vue'
import LogoCSUCC from '@/assets/logo/Csucc.png'
import BcCSUCC from '@/assets/logo/bccsucc.png'
import WebLogo from '@/assets/logo/weblogo.png'

const theme = ref('light')

function onClick() {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}
const visible = ref(false)
</script>
<template>
  <v-responsive>
    <v-app :theme="theme">
      <v-app-bar class="px-3">
        <v-spacer></v-spacer>
        <div class="top-left">
          <v-img :src="WebLogo" width="150" height="auto" class="logo"></v-img>
        </div>

        <v-btn
          :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          text="Toggle Theme"
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
              <div>
                <div class="d-flex align-center justify center">
                  <!-- <v-img :src="LogoCSUCC" contain width="200" height="200"> </v-img> -->
                  <v-img :src="LogoCSUCC" contain width="200" height="200"> </v-img>
                </div>
                <v-btn
                  class="mt-5"
                  size="x-large"
                  color="blue"
                  elevation="10"
                  :to="{ name: 'home' }"
                >
                  Back to Home
                </v-btn>
              </div>

              <div>
                <v-card class="mx-auto pa-12 pb-8" elevation="8" max-width="448" rounded="lg">
                  <div class="text-subtitle-1 text-medium-emphasis">Account</div>

                  <v-text-field
                    density="compact"
                    placeholder="Email address"
                    prepend-inner-icon="mdi-email-outline"
                    variant="outlined"
                  ></v-text-field>

                  <div
                    class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between"
                  >
                    Password

                    <a
                      class="text-caption text-decoration-none text-blue"
                      href="#"
                      rel="noopener noreferrer"
                      target="_blank"
                    >
                      Forgot login password?</a
                    >
                  </div>

                  <v-text-field
                    :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
                    :type="visible ? 'text' : 'password'"
                    density="compact"
                    placeholder="Enter your password"
                    prepend-inner-icon="mdi-lock-outline"
                    variant="outlined"
                    @click:append-inner="visible = !visible"
                  ></v-text-field>

                  <v-card class="mb-12" color="surface-variant" variant="tonal">
                    <v-card-text class="text-medium-emphasis text-caption">
                      Warning: After 3 consecutive failed login attempts, you account will be
                      temporarily locked for three hours. If you must login now, you can also click
                      "Forgot login password?" below to reset the login password.
                    </v-card-text>
                  </v-card>

                  <v-btn class="mb-8" color="blue" size="large" variant="tonal" block>
                    Log In
                  </v-btn>

                  <v-card-text class="text-center">
                    <a
                      class="text-blue text-decoration-none"
                      href="#"
                      rel="noopener noreferrer"
                      target="_blank"
                    >
                      Sign up now <v-icon icon="mdi-chevron-right"></v-icon>
                    </a>
                  </v-card-text>
                </v-card>
              </div>
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
  display: fkex;
  align-items: center;
  padding: 0.5rem;
  gap: 0.5rem;
}
h1 {
  color: white;
}
</style>
