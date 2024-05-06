<template>
  <div id="app">
    <!-- Header -->
    <header class="p-3 bg-dark text-white text-center">
      <h1>Aplikasi Penjadwalan Kuliah</h1>
    </header>

    <div class="container-fluid">
      <div class="row">
        <!-- Left Navigation -->
        <nav class="col-md-3 col-lg-2 d-md-block bg-light sidebar">
          <div class="position-sticky">
            <ul class="nav flex-column">
              <li class="nav-item" >
                <a class="nav-link" href="#" @click="changeContent('Home')"> Home</a>
              </li>
              <li class="nav-item" >
                <a class="nav-link" href="#" @click="changeContent('Dosen')"> Dosen</a>
              </li>
              <li class="nav-item" >
                <a class="nav-link" href="#" @click="changeContent('Mahasiswa')"> Mahasiswa</a>
              </li>
              <li class="nav-item" >
                <a class="nav-link" href="#" @click="changeContent('Ruangan')"> Ruangan</a>
              </li>
            </ul>
          </div>
        </nav>

        <!-- Content -->
        <main class="col-md-9 ms-sm-auto col-lg-10 px-md-4">
          <component :is="currentComponent"></component>
        </main>
      </div>
    </div>
  </div>
</template>

<script>
import Home from './components/HomeComponent.vue';
import Mahasiswa from './components/MahasiswaComponent.vue';
import Dosen from './components/DosenComponent.vue';
import Ruangan from './components/RuanganComponent.vue';

export default {
  name: 'App',
  components: {
    Home,
    Mahasiswa,
    Dosen,
    Ruangan
  },
  data() {
    return {
      currentComponent: 'Home' // Komponen yang sedang ditampilkan secara default
    }
  },
  methods: {
    changeContent(componentName) {
      this.currentComponent = componentName;
    }
  }
}
</script>

<style scoped>
/* Gaya khusus untuk komponen ini */
.sidebar {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  z-index: 100;
  padding: 48px 0 0;
  box-shadow: inset -1px 0 0 rgba(0, 0, 0, 0.1);
}

@media (min-width: 768px) {
  .sidebar {
    width: 230px;
  }
}
</style>