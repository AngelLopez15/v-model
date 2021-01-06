<template>
  <h1 class="is-size-1 has-text-centered">Formulario con Vue</h1>
  <form 
    class="container"
    @submit.prevent="procesarFormulario"
  >
    <Input :tarea="tarea" />
  </form>
  <hr>
  <ListaTarea />
</template>

<script>
import Input from '../components/Input'
import ListaTarea from '../components/ListaTarea'
import {mapActions} from 'vuex'
let shortid = require('shortid');
export default {
  name: 'Home',
  components: {
    Input,
    ListaTarea
  },
  data() {
    return {
      tarea: {
        id:'',
        nombre:'',
        categorias:[],
        estado:'',
        numero:0
      }
    }
  },
  methods:{
    ...mapActions(['setTareas']),
    procesarFormulario(){
      console.log(this.tarea)
      if (this.tarea.nombre.trim()==="") {
        console.log('Campo vacio')
        return
      }
      console.log('Campos llenos')
      
      // generar id
      this.tarea.id = shortid.generate()

      // enviar los datos
      this.setTareas(this.tarea)
      // Limpiar los campos una vez los datos se hayan enviado
      this.tarea = {
        id:'',
        nombre:'',
        categorias:[],
        estado:'',
        numero:0
      }
    }
  },
}
</script>
