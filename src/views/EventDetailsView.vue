<script setup>
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService.js'

const props = defineProps({
    id: {
      required: true
    }
  
});

const event = ref(null)

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
</script>

<template>
  <div v-if="event">
    <h2>{{ event.title }}</h2>
    <span>{{ event.description }}</span>
    <span>{{ event.date }} on {{ event.time }} @ {{ event.location }}</span>
    <span>{{ event.petsAllowed }}</span>
    <span>{{ event.organizer }}</span>
  </div>
</template>
