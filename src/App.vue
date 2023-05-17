<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <nav class="navbar bg-primary" data-bs-theme="dark">
  <div class="container-fluid">
    <img src="../src/assets/quran.png" width="70" height="70" alt="" title="" class="img-small">
    <a class="navbar-brand" href="/" >Al-Qur'an Digital</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <a class="nav-link" href="/surah">Daftar Surah</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="/about">Keutamaan Membaca Al-Qur'an</a>
        </li>
        <form class="d-flex" role="search">
      <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" style="background-color: white;" v-model="Search" @input="">
      <button class="btn btn-outline-success" type="submit" style="background-color: white; color: black;">Search</button>
    </form>
      </ul>
      
    </div>
    
  </div>
</nav>
  </header>

  <RouterView />
</template>

<style scoped>
.navbar-brand{
  margin-left: 10px;
}

.navbar-nav{
  margin-left: 30%;
}
</style>
