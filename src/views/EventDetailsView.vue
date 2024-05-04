<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'
import EventService from '@/services/EventService.js'

const props = defineProps({
    id: {
      required: true
    }
  
});

const event = ref(null)
const router = useRouter()

onMounted(() => {
  EventService.getEvent(props.id)
    .then((response) => {
      // console.log('events :', response.data)
      event.value = response.data
    })
    .catch((error) => {
      console.error('Error fetching events:', error)
    })
})

const goBackToList = () => {
  router.push({ name: 'event-list' })
}
</script>

<template>
  <div v-if="event" class="event-details-container">
    <h2 class="event-title">{{ event.title }}</h2>
    <p class="event-description">{{ event.description }}</p>
    <p class="event-info">{{ event.date }} pada {{ event.time }} di {{ event.location }}</p>
    <p class="event-pets">{{ event.petsAllowed ? 'Hewan Peliharaan Diperbolehkan' : 'Hewan Peliharaan Tidak Diperbolehkan' }}</p>
    <p class="event-organizer">Penyelenggara: {{ event.organizer }}</p>
    <button @click="goBackToList" class="back-button">Kembali ke Daftar</button>
  </div>
</template>

<style scoped>
.event-details-container {
  padding: 20px;
  background-color: #f0f4f8;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  margin-top: 20px;
}

.event-title {
  color: #333;
  font-size: 24px;
  margin-bottom: 10px;
}

.event-description {
  color: #666;
  font-size: 16px;
  margin-bottom: 10px;
}

.event-info {
  color: #444;
  font-size: 14px;
  margin-bottom: 10px;
}

.event-pets {
  color: #787878;
  font-size: 14px;
  margin-bottom: 10px;
}

.event-organizer {
  color: #2a9d8f;
  font-size: 14px;
  font-style: italic;
  margin-bottom: 10px;
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