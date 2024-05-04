<script setup>
defineProps({
  resource: {
    type: String,
    required: true,
    default: 'page'
  }
})
</script>

<template>
  <div class="not-found-container">
    <h1>Oops!</h1>
    <h3>Halaman {{ resource }} yang Anda cari tidak ditemukan.</h3>
    <router-link :to="{ name: 'event-list' }" class="home-button">Kembali ke Beranda</router-link>
  </div>
</template>

<style scoped>
.not-found-container {
  text-align: center;
  padding: 50px;
  background-color: #f8f9fa;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.home-button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.home-button:hover {
  background-color: #0056b3;
}
</style>