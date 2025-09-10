<template>
  <div class="d-flex">
    <Sidebar @change-section="section = $event" />
    <div class="flex-grow-1 p-4">
      <component :is="section" />
    </div>
  </div>
</template>

<script>
import Sidebar from './components/Sidebar.vue'
import LandingPage from './components/LandingPage.vue'
import Clientes from './components/Clientes.vue'

export default {
  components: { Sidebar, LandingPage, Clientes },
  data() {
    return {
      section: 'LandingPage'
    }
  }
}
</script>

<style>
body {
  font-family: 'Arial', sans-serif;
}
</style>
