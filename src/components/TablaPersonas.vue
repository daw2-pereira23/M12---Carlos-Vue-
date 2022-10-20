<template>
  <div id="tabla-personas">
    <div v-if="!personas.length" class="alert alert-info" role="alert">
      No se han agregado personas
    </div>
    <table class="table">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Apellido</th>
          <th>Email</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="persona in personas" :key="persona.id">
          <td v-if="editando === persona.id">
              <input type="text" class="form-control" v-model="persona.nombre" />
          </td>
          <td v-else>
              {{ persona.nombre}}
          </td>
          <td v-if="editando === persona.id">
              <input type="text" class="form-control" v-model="persona.apellido" />
          </td>
          <td v-else>
              {{ persona.apellido}}
          </td>
          <td v-if="editando === persona.id">
              <input type="email" class="form-control" v-model="persona.email" />
          </td>
          <td v-else>
              {{ persona.email}}
          </td>
          <td>
                <button class="btn btn-info" @click="editarPersona(persona)">✏️ Editar</button>
                <button class="btn btn-danger ml-2" @click="$emit('delete-persona', persona.id)">🗑️ Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
  export default {
  name: 'tabla-personas',
  props: {
    personas: Array,
  },
}
</script>

<style scoped></style>