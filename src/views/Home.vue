<template>
  <h1 class="my-5 text-center">Todo list with Vue.JS</h1>

  <form @submit.prevent="procesarFormulario">
    <Input :tarea="tarea" />
  </form>
  <hr />
  <lista-tareas></lista-tareas>
</template>

<script>
import Input from "../components/Input.vue";
import { mapActions } from "vuex";
import shortid from "shortid";
import ListaTareas from "../components/ListaTareas.vue";

export default {
  name: "Home",
  components: {
    Input,
    ListaTareas,
  },
  data() {
    return {
      tarea: {
        id: "",
        nombre: "",
        categorias: [],
        importancia: "",
        hora: Date(),
      },
    };
  },
  methods: {
    ...mapActions(["setTareas"]),
    procesarFormulario() {
      console.log(this.tarea);
      if (this.tarea.nombre.trim() === "") {
        console.log("Campo vacío");
        return;
      }
      console.log("no está vacio");

      // generar id
      this.tarea.id = shortid.generate();
      console.log(this.tarea.id);

      this.setTareas(this.tarea);

      // envian los datos

      this.tarea = {
        id: "",
        nombre: "",
        categorias: [],
        importancia: "",
        hora: Date,
      };
    },
  },
};
</script>
