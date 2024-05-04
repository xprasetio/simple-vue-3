<script setup>
defineProps({
  event: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <RouterLink  class="event-link" :to="{ name: 'event-details', params: { id: event.id } }">
    <div class="event-card">
      <h2>{{ event.title }}</h2>
      <span>{{ event.description }}</span>
      <span>{{ event.location }}</span>
      <span>{{ event.date }}</span>
      <span>{{ event.time }}</span>
      <span>{{ event.petsAllowed }}</span>
      <span>{{ event.organizer }}</span>
      <!-- Display event card  -->
    </div>
  </RouterLink>
</template>

<style scoped>
.event-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
}

.event-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}
.event-link {
  color: #39495c;
  text-decoration: none;
}
</style>
