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
              <div>
                <div class="d-flex align-center justify center">
                  <v-img :src="LogoCSUCC" contain width="200" height="200"> </v-img>
                </div>
              </div>

              <div>
                <v-card class="mx-auto pa-16 pb-8" elevation="8" max-width="448" rounded="xl">
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
                      <v-divider class="my-5"></v-divider>

                      <h5>
                        <RouterLink to="forgotpassword">Forgot login password?</RouterLink>
                      </h5>
                    </a>
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
                  <v-btn class="mb-8" color="blue" size="large" variant="tonal" block rounded="xl">
                    Log In
                  </v-btn>

                  <v-card-text class="text-center">
                    <v-btn
                      class="mt-5"
                      size="x-large"
                      color="blue"
                      elevation="10"
                      :to="{ name: 'home' }"
                      rounded="xl"
                    >
                      Back to Home
                    </v-btn>

                    <v-divider class="my-5"></v-divider>

                    <h5>
                      Don't have an account?
                      <RouterLink to="signup">Click here to Registre</RouterLink>
                    </h5>
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
  display: flex;
  align-items: center;
  padding: 0.5rem;
  gap: 0.5rem;
}
h1 {
  color: white;
}
</style>
