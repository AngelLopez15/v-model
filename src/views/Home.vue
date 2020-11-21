<template>
  
  <form 
    class="container"
    @submit.prevent="procesarFormulario"
  >

    <div class="column is-half is-offset-one-quarter">
      <div class="field">
        <label class="label">Nombre</label>
        <div class="control">
          <input 
            class="input" 
            type="text" 
            placeholder="Ingrese nombre"
            v-model.trim="tarea.nombre"
          >
        </div>
      </div>

      <div class="field">
        <label class="label">Numero</label>
        <input 
          class="input is-success" 
          type="number" 
          placeholder="123456"
          v-model.number="tarea.numero"
        >
      </div>

      <!-- <div class="field">
        <label class="label">Username</label>
        <div class="control has-icons-left has-icons-right">
          <input class="input is-success" type="text" placeholder="Text input" >
          <span class="icon is-small is-left">
            <i class="fas fa-user"></i>
          </span>
          <span class="icon is-small is-right">
            <i class="fas fa-check"></i>
          </span>
        </div>
        <p class="help is-success">This username is available</p>
      </div> -->

      <!-- <div class="field">
        <label class="label">Email</label>
        <div class="control has-icons-left has-icons-right">
          <input class="input is-danger" type="email" placeholder="Email input" >
          <span class="icon is-small is-left">
            <i class="fas fa-envelope"></i>
          </span>
          <span class="icon is-small is-right">
            <i class="fas fa-exclamation-triangle"></i>
          </span>
        </div>
        <p class="help is-danger">This email is invalid</p>
      </div> -->

      <!-- <div class="field">
        <label class="label">Subject</label>
        <div class="control">
          <div class="select">
            <select>
              <option>Select dropdown</option>
              <option>With options</option>
            </select>
          </div>
        </div>
      </div> -->

      <!-- <div class="field">
        <label class="label">Message</label>
        <div class="control">
          <textarea class="textarea" placeholder="Textarea"></textarea>
        </div>
      </div> -->

      <div class="field">
        <div class="control">
          <label class="checkbox mx-1">
            <input 
              type="checkbox"
              value="javascript"
              v-model="tarea.categorias"
            >
            JavaScrip
          </label>
          <label class="checkbox mx-1">
            <input 
              type="checkbox"
              value="node js"
              v-model="tarea.categorias"
            >
            Node Js
          </label>
        </div>
      </div>

      <div class="field">
        <div class="control">
          <label class="radio">
            <input 
              type="radio"
              name="question"
              value="Si"
              v-model="tarea.estado"
            >
            Si
          </label>
          <label class="radio">
            <input 
              type="radio"
              name="question"
              value="No"
              v-model="tarea.estado"
            >
            No
          </label>
        </div>
      </div>

      <div class="field">
        <div class="control">
          <button 
            class="button is-dark is-rounded is-fullwidth" 
            type="submit"
            :disabled="bloquear"
          >
            Procesar
          </button>
        </div>
        <!-- <div class="control">
          <button class="button is-link is-light">Cancel</button>
        </div> -->
      </div>
    </div>
    
  </form>

</template>

<script>

export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      tarea: {
        nombre:'',
        categorias:[],
        estado:'',
        numero:0
      }
    }
  },
  methods:{
    procesarFormulario(){
      console.log(this.tarea)
      if (this.tarea.nombre.trim()==="") {
        console.log('Campo vacio')
        return
      }
      console.log('Campos llenos')
      
      // Limpiar los campos una vez los datos se hayan enviado
      this.tarea = {
        nombre:'',
        categorias:[],
        estado:'',
        numero:0
      }
    }
  },
  computed:{
    bloquear(){
      return this.tarea.nombre.trim() === "" ? true : false
    }
  }
}
</script>
