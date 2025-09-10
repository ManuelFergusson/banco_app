<template>
  <form @submit.prevent="save">
    <div class="mb-2">
      <input type="text" v-model="nombre" class="form-control" placeholder="Nombre" required />
    </div>
    <div class="mb-2">
      <input type="email" v-model="correo" class="form-control" placeholder="Correo" required />
    </div>
    <div class="mb-2">
      <input type="text" v-model="telefono" class="form-control" placeholder="Teléfono" required />
    </div>
    <button type="submit" class="btn btn-primary">Guardar</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      nombre: '',
      correo: '',
      telefono: ''
    }
  },
  methods: {
    save() {
      this.$emit('save-client', {
        nombre: this.nombre,
        correo: this.correo,
        telefono: this.telefono
      })
      this.nombre = ''
      this.correo = ''
      this.telefono = ''
    }
  }
}
</script>
