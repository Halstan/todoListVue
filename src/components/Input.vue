<template>
  <input
    type="text"
    class="form-control my-2"
    placeholder="Ingrese nombre"
    v-model.trim="tareaObj.nombre"
  />

  <div class="form-check form-check-inline">
    <input
      type="checkbox"
      id="check-1"
      class="form-check-input"
      v-model="tareaObj.categorias"
      value="javascript"
    />
    <label for="check-1" class="form-check-label">Javascript</label>
  </div>
  <div class="form-check form-check-inline">
    <input
      type="checkbox"
      id="check-2"
      class="form-check-input"
      v-model="tareaObj.categorias"
      value="node js"
    />
    <label for="check-2" class="form-check-label">Node.js</label>
  </div>

  <div class="mt-2">
    <select class="form-control form-select-lg" v-model="tareaObj.importancia">
      <option value="" disabled selected>--Elija una opcion--</option>
      <option value="bajo">Bajo</option>
      <option value="medio">Medio</option>
      <option value="alto">Alto</option>
    </select>
    <!--
    <div class="form-check form-check-inline">
      <input
        type="radio"
        id="radio-1"
        class="form-check-input"
        value="urgente"
        v-model="tareaObj.estado"
      />
      <label for="radio-1" class="form-check-label">Urgente</label>
    </div>
    <div class="form-check form-check-inline">
      <input
        type="radio"
        id="radio-2"
        class="form-check-input"
        value="relax"
        v-model="tareaObj.estado"
      />
      <label for="radio-2" class="form-check-label">Relax</label>
    </div>-->
  </div>

  <div class="mt-2">
    <input type="date" class="form-control" v-model.number="tareaObj.hora" />
  </div>

  <div class="mt-2">
    <div class="form-check form-check-inline">
      <input
        type="radio"
        id="radio-1"
        class="form-check-input"
        value="true"
        v-model="tareaObj.isFinish"
      />
      <label for="radio-1" class="form-check-label">Terminado</label>
    </div>
    <div class="form-check form-check-inline">
      <input
        type="radio"
        id="radio-2"
        class="form-check-input"
        value="falso"
        v-model="tareaObj.isFinish"
      />
      <label for="radio-2" class="form-check-label">Incompleto</label>
    </div>
  </div>

  <button
    class="btn btn-dark mt-2 btn-block"
    type="submit"
    :disabled="bloquear"
  >
    Procesar
  </button>
</template>

<script>
export default {
  name: "Input",
  data() {
    return {
      tareaObj: this.tarea,
    };
  },
  props: {
    tarea: Object,
  },
  computed: {
    bloquear() {
      return this.tarea.nombre.trim() === "";
    },
  },
};
</script>
