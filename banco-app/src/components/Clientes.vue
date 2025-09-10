<template>
  <div class="container mt-4">
    <h2 class="mb-3">Mantenimiento de Clientes</h2>
    
    <ClienteForm @save-client="addClient" />

    <table class="table table-striped mt-3">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Correo</th>
          <th>Teléfono</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="client in clients" :key="client.id">
          <td>{{ client.nombre }}</td>
          <td>{{ client.correo }}</td>
          <td>{{ client.telefono }}</td>
          <td>
            <button class="btn btn-warning btn-sm me-1" @click="editClient(client)">Editar</button>
            <button class="btn btn-danger btn-sm" @click="deleteClient(client.id)">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'
import ClienteForm from './ClienteForm.vue'

export default {
  components: { ClienteForm },
  data() {
    return {
      clients: [],
      apiUrl: 'http://127.0.0.1:8000/api/clientes/'
    }
  },
  mounted() {
    this.getClients()
  },
  methods: {
    async getClients() {
      try {
        const res = await axios.get(this.apiUrl)
        this.clients = res.data
      } catch (error) {
        console.error(error)
      }
    },
    async addClient(cliente) {
      try {
        await axios.post(this.apiUrl, cliente)
        this.getClients()
      } catch (error) {
        console.error(error)
      }
    },
    async deleteClient(id) {
      try {
        await axios.delete(`${this.apiUrl}${id}/`)
        this.getClients()
      } catch (error) {
        console.error(error)
      }
    },
    async editClient(client) {
      const nombre = prompt("Editar nombre", client.nombre)
      const correo = prompt("Editar correo", client.correo)
      const telefono = prompt("Editar teléfono", client.telefono)
      if(nombre && correo && telefono){
        try {
          await axios.put(`${this.apiUrl}${client.id}/`, {nombre, correo, telefono})
          this.getClients()
        } catch (error) {
          console.error(error)
        }
      }
    }
  }
}
</script>
