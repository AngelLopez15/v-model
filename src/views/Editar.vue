<template>
  <p class="is-size-1 has-text-centered">Editar {{$route.params.id}}</p>
  <form @submit.prevent="updateTarea(tarea)">
    <Input :tarea="tarea" />
  </form>
</template>

<script>
import {mapState, mapActions} from 'vuex'
import Input from '../components/Input'
export default {
  components:{
    Input
  },
  computed: {
    ...mapState(['tarea'])
  },
  methods: {
    ...mapActions(['setTarea', 'updateTarea'])
  },
  created(){
    this.setTarea(this.$route.params.id)
  }
}
</script>