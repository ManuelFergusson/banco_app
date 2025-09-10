<template>
  <div class="bg-primary text-white vh-100 p-3 sidebar">
    <h4 class="mb-4">Banco G&T </h4>
    <ul class="nav flex-column">
      <li class="nav-item mb-2" @click="$emit('change-section','LandingPage')">
        <i class="fas fa-home me-2"></i> Inicio
      </li>
      <li class="nav-item mb-2" @click="$emit('change-section','Clientes')">
        <i class="fas fa-users me-2"></i> Clientes
      </li>
    </ul>
  </div>
</template>

<style>
.sidebar {
  width: 220px;
}
.nav-item {
  cursor: pointer;
  padding: 10px;
  border-radius: 5px;
}
.nav-item:hover {
  background-color: rgba(255,255,255,0.2);
}
</style>
