<template>
  <q-layout view="lHh lpR fFf">
    <!-- Navbar -->
    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered class="bg-primary text-white">
      <q-list>
        <q-item clickable v-ripple @click="selectedTab = 'beranda'">
          <q-item-section>Beranda</q-item-section>
        </q-item>
        <q-item clickable v-ripple @click="selectedTab = 'terlaris'">
          <q-item-section>Terlaris</q-item-section>
        </q-item>
        <q-item clickable v-ripple @click="selectedTab = 'keranjang'">
          <q-item-section>Keranjang</q-item-section>
        </q-item>
        <q-item clickable v-ripple @click="selectedTab = 'pesan'">
          <q-item-section>Pesan</q-item-section>
        </q-item>
        <q-item clickable v-ripple @click="selectedTab = 'ulasan'">
          <q-item-section>Ulasan</q-item-section>
        </q-item>
      </q-list>
    </q-drawer

    <!-- Content -->
    <q-page-container>
      <q-header elevated class="bg-primary text-white">
        <q-toolbar>
          <q-btn dense flat round icon="Menu" @click="toggleLeftDrawer" />
          <q-toolbar-title>
            <q-avatar>
              <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
            </q-avatar>
            PAI Electronik Store
          </q-toolbar-title>
        </q-toolbar>
      </q-header>

      <!-- Carousel -->
      <q-carousel v-model="slide" arrows animated infinite>
        <q-carousel-slide name="1" img-src="./assets/1.jpeg">
          <div class="absolute-bottom text-center text-h5 text-white bg-black bg-opacity-50 full-width q-pa-md slide-in">
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="2" img-src="./assets/3.jpeg">
          <div class="absolute-bottom text-center text-h5 text-white bg-black bg-opacity-50 full-width q-pa-md slide-in">
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="3" img-src="./assets/a1.jpeg">
          <div class="absolute-bottom text-center text-h5 text-white bg-black bg-opacity-50 full-width q-pa-md slide-in">
          </div>
        </q-carousel-slide>
      </q-carousel>

      <!-- Product Categories -->
      <div class="q-pa-md">
        <div class="text-h5 q-mb-md">Categories</div>
        <div class="row q-col-gutter-md q-gutter-sm">
          <q-card class="col-xs-12 col-sm-6 col-md-4">
            <q-img src="./assets/1.jpeg">
              <q-card-section>
                <div class="text-h6">ThinkPad X1 Yoga Gen 7</div>
              </q-card-section>
            </q-img>
          </q-card>
          <q-card class="col-xs-12 col-sm-6 col-md-4">
            <q-img src="./assets/3.jpeg">
              <q-card-section>
                <div class="text-h6">HP 14s-dq2575TU</div>
              </q-card-section>
            </q-img>
          </q-card>
          <q-card class="col-xs-12 col-sm-6 col-md-4">
            <q-img src="./assets/a1.jpeg">
              <q-card-section>
                <div class="text-h6">MSI Modern 14 B1OMW-281</div>
              </q-card-section>
            </q-img>
          </q-card>
        </div>
      </div>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)
    const rightDrawerOpen = ref(false)
    const slide = ref('1')
    const selectedTab = ref('beranda')

    return {
      leftDrawerOpen,
      rightDrawerOpen,
      slide,
      selectedTab,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      toggleRightDrawer () {
        rightDrawerOpen.value = !rightDrawerOpen.value
      }
    }
  }
}
</script>

<style scoped>
.bg-gradient {
  background: linear-gradient(90deg, #00988f, #ff9a8b) !important;
}
.q-carousel-slide {
  height: 400px;
}

.absolute-bottom {
  position: absolute;
  bottom: 0;
  width: 100%;
  text-align: center;
}
.bg-opacity-50 {
  background-color: rgba(0, 0, 0, 0.5);
}
.slide-in {
  animation: slide-in 1s ease;
}
@keyframes slide-in {
  0% {
    transform: translateY(100%);
  }
  100% {
    transform: translateY(0);
  }
}
</style>
