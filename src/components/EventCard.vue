<script setup>
defineProps({
  event: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <RouterLink class="event-link" :to="{ name: 'event-details', params: { id: event.id } }">
    <div class="event-card">
      <h2>{{ event.title }}</h2>
      <p>{{ event.description }}</p>
      <div class="event-details">
        <span class="event-location">{{ event.location }}</span>
        <span class="event-date">{{ event.date }}</span>
        <span class="event-time">{{ event.time }}</span>
        <span class="event-pets">{{ event.petsAllowed ? 'Pets Allowed' : 'No Pets Allowed' }}</span>
        <span class="event-organizer">{{ event.organizer }}</span>
      </div>
    </div>
  </RouterLink>
</template>

<style scoped>
.event-card {
  padding: 20px;
  width: 300px;
  cursor: pointer;
  border: 2px solid #39495c;
  border-radius: 8px;
  background-color: #f9f9f9;
  margin-bottom: 20px;
  transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
}

.event-card:hover {
  transform: scale(1.03);
  box-shadow: 0 4px 15px 0 rgba(57, 73, 92, 0.3);
}

.event-link {
  color: #39495c;
  text-decoration: none;
}

.event-details {
  margin-top: 10px;
}

.event-location, .event-date, .event-time, .event-pets, .event-organizer {
  display: block;
  margin-top: 5px;
  font-size: 14px;
  color: #333;
}

.event-location {
  font-weight: bold;
  color: #2a9d8f;
}

.event-date, .event-time {
  color: #e76f51;
}

.event-pets {
  color: #264653;
}

.event-organizer {
  font-style: italic;
  color: #2a9d8f;
}
</style>
