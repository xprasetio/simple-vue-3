<script setup>
import { useRouter } from 'vue-router'
import { defineProps, inject } from 'vue'

const {event} = defineProps(['event']);
const router = useRouter()
const GStore = inject('GStore')

const register = () => {
  GStore.flashMessage = 'You are successfully registered for ' + event.title
  setTimeout(() => {
    GStore.flashMessage = ''
  }, 3000)
  router.push({
    name: 'event-details'
  })
}
</script>
<template>
  <p>Register for the event here</p>
  <button class="back-button" @click="register">Back</button>
  <div v-if="GStore.flashMessage" class="flash-message">{{ GStore.flashMessage }}</div>
</template>

<style scoped>
.back-button {
  padding: 10px 20px;
  margin: 0 10px; /* Menambahkan margin kanan dan kiri 10px */
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.back-button:hover {
  background-color: #367b59;
}

.flash-message {
  padding: 10px;
  margin-top: 20px;
  background-color: #f4f4f4;
  color: #333;
  border: 1px solid #ccc;
  border-radius: 5px;
  text-align: center;
  animation: fadeOut 3s forwards;
}

@keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
</style>
