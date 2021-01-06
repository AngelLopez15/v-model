<template>
<table class="table">
  <thead>
    <tr>
      <th>id</th>
      <th>Nombre</th>
      <th>Categoria</th>
      <th>Estado</th>
      <th>Numero</th>
      <th>Accion</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="item in tareas" :key="item.id">
      <td>{{item.id}}</td>
      <td>{{item.nombre}}</td>
      <td>
        <span v-for="(cat, index) in item.categorias" :key="index">
          {{
            (item.categorias.length === index + 1) ? cat : `${cat}, ` 
          }}
        </span>
      </td>
      <td>{{item.estado}}</td>
      <td>{{item.numero}}</td>
      <td>
        <button class="button is-danger is-small" @click="deleteTareas(item.id)">Eliminar</button>
        <router-link :to="{name: 'Editar', params: {id: item.id } }" class="button is-primary is-small">
          Editar
        </router-link>
      </td>
    </tr>
  </tbody>
</table>
</template>

<script>
import {mapState, mapActions} from 'vuex'
export default {
  computed: {
    ...mapState(['tareas'])
  },
  methods: {
    ...mapActions(['deleteTareas'])
  },
}
</script>