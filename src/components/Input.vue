<template>
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
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tarea: Object
  },
  computed:{
    bloquear(){
      return this.tarea.nombre.trim() === "" ? true : false
    }
  }
} 
</script>