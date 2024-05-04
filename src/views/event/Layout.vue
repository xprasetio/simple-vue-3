<script setup>
import { ref, onMounted, computed, defineProps } from 'vue'
import { useRouter } from 'vue-router'
import EventService from '@/services/EventService.js'

const props = defineProps(['id'])

const id = computed(() => props.id)

const event = ref(null)

const router = useRouter()

onMounted(() => {
  EventService.getEvent(id.value)
    .then((response) => {
      event.value = response.data
    })
    .catch((error) => {
      if (error.response && error.response.status == 404) {
        router.push({
          name: '404Resource',
          params: { resource: 'event' }
        })
      } else {
        router.push({ name: 'NetworkError' })
      }
    })
})

const goBackToList = () => {
  router.push({ name: 'event-list' })
}
</script>

<template>
  <div v-if="event" class="event-details-container">
    <h2 class="event-title">{{ event.title }}</h2>
    <div id="nav" class="navbar">
      <router-link :to="{ name: 'event-details' }">
        <button class="details-button">Detail Acara</button>
      </router-link>
      <router-link :to="{ name: 'event-register' }">
        <button class="register-button">Register Acara</button>
      </router-link>
      <router-link :to="{ name: 'event-edit' }">
        <button class="edit-button">Edit Acara</button>
      </router-link>
    </div>
    <router-view :event="event" />
    <button @click="goBackToList" class="back-button">Kembali ke Daftar</button>
  </div>
</template>

<style scoped>
.event-details-container {
  padding: 20px;
  background-color: #f0f4f8;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-top: 20px;
}

.event-title {
  color: #333;
  font-size: 24px;
  margin-bottom: 10px;
}

.navbar {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.details-button,
.register-button,
.edit-button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-right: 10px;
}

.details-button {
  background-color: #42a5f5;
}

.register-button {
  background-color: #66bb6a;
}

.edit-button {
  background-color: #ffa726;
}

.details-button:hover,
.register-button:hover,
.edit-button:hover {
  color: white;
}

.back-button {
  padding: 10px 20px;
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
</style>
