<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { inject } from 'vue'

const GStore = inject('GStore')
</script>

<template>
  <div id="layout">
    <div id="flashMessage" v-if="GStore.flashMessage" class="flash-message">{{ GStore.flashMessage }}</div>
    <header>
      <div class="wrapper">
        <nav>
          <button class="tab-button">
            <RouterLink class="nav-link" :to="{ name: 'event-list' }">Events</RouterLink>
          </button>
          |
          <button class="tab-button">
            <RouterLink class="nav-link" :to="{ name: 'about' }">About</RouterLink>
          </button>
        </nav>
      </div>
    </header>
    <RouterView />
  </div>
</template>

<style>
@keyframes yellowfade {
  from {
    background-color: #42b983;
  }
  to {
    background-color: transparent;
  }
}

#layout {
  font-family: Avenir, Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
nav {
  padding: 30px;
}
nav .nav-link {
  font-weight: bold;
  color: #2c3e50;
  padding: 10px 15px;
  transition:
    background-color 0.3s,
    color 0.3s;
}
nav .nav-link:hover {
  background-color: #42b983;
  color: #fff;
}
nav .router-link-exact-active {
  color: #42b983;
}
nav .tab-button {
  background: none;
  border: none;
  cursor: pointer;
}
h2 {
  font-size: 20px;
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
